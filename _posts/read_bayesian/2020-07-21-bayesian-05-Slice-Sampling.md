---
title: "「Bayesian」5 Slice Sampling"
subtitle: "Slice Sampling - Implication"
layout: post
author: "Linsui"
header-style: text
tags:
  - Bayesian
  - R language
  - Course
  - 笔记
---

# Slice Sampling: Implementation

Library Pakages:

```R
library(ggplot2)
set.seed(0)
```

Generate from the density 
---------------------------------------------------------------------------

Generate from the density $f(x)=(1/2)e^{-\sqrt{x}}\boldsymbol{1}(x>0)$: 

- $U\mid x \sim \mathcal{U}\left(0, \frac{1}{2} e^{-\sqrt{x}}\right)$; 
- $X\mid u \sim \mathcal{U}\left(0,[\log (2 u)]^{2}\right)$

Define the maximum value of the uniform distribution.

```R
f_x <- function(x){
  return(exp(-sqrt(x))/2.0)
}

g_u <- function(u){
  return((log(2.0*u))^2)
}
```

Generate the samples.

```R
# Set the generation rounds and initial value
times <- 500
X_U <- data.frame(X=numeric(times),U=numeric(times))
X_U$X[0] <- 0

# Sampling Procedure
for(i in c(2:times)){
  X_U$U[i] <- runif(1,min=0,max=f_x(X_U$X[i-1]))
  X_U$X[i] <- runif(1,min=0,max=g_u(X_U$U[i]))
}
```

Plot the result:

```R
X_U$U_line <- f_x(X_U$X)
    
ggplot(data=X_U)+
  geom_point(aes(x=X,y=U),colour="#6495ED",alpha = 0.5, size=1)+
  geom_line(aes(x=X,y=U_line),size=1)
```

![](/img/in-post/Bayesian/sample12-1.png)

Generate from the truncated normal density
------------------------------------------

Our target density is: $f(x) \propto f_{1}(x)=\exp \{-(x+3)^{2} / 2\} \mathbb{I}_{[0,1]}(x)$

- $U\mid x \sim \mathcal{U}\left(0, \exp \{-(x+3)^{2} / 2\}\right)$
- $X\mid u\sim\{y ; \exp \{-(y+3)^{2} / 2\} \geq u\}\cap[0,1]$

Define the specific values for generating the uniform distribution.

```R
f_x <- function(x){
  return(exp(-(x+3)^2/2.0))
}

g_u <- function(u){
  return(sqrt(-2*log(u)))
}
```

Generate the samples.

```R
# Set the generation rounds and initial value
times <- 500
X_U <- data.frame(X=numeric(times),U=numeric(times))
X_U$X[0] <- 0

# Sampling Procedure
for(i in c(2:times)){
  X_U$U[i] <- runif(1,min=0,max=f_x(X_U$X[i-1]))
  X_U$X[i] <- runif(1,
                    min=max(c(0,-3-g_u(X_U$U[i]))),
                    max=min(c(1,-3+g_u(X_U$U[i]))))
}
```

Plot the result:

```R
X_U$U_line <- f_x(X_U$X)
    
ggplot(data=X_U)+
  geom_point(aes(x=X,y=U),colour="#6495ED",alpha = 0.5, size=1)+
  geom_line(aes(x=X,y=U_line),size=1)
```

![](/img/in-post/Bayesian/sample22-1.png)

A 3D slice sampler
------------------

Generate from the density:
$$
f(x)=\exp \left(-x^{2} / 2\right) \times(1+\cos (\pi x)) \times \mathrm{I}(x \in[-0.5,0.5])
$$


- Step 1: generate $\omega\mid x$
  - $\omega_1\sim U[0,\exp(-x^2/2)]$
  - $\omega_2\sim U[0,1+\cos(\pi x)]$
- Step 2: generate $x'\mid \omega$
  - $I_1=[-\sqrt{2\log(\omega_1)},\sqrt{2\log(\omega_1)}]$
  - $I_2=[-\frac{\arccos(\omega_2'-1)}{\pi},\frac{\arccos(\omega_2'-1)}{\pi}]$
  - $I_3=[-0.5,0.5]$
  - $x'\sim \boldsymbol{1}_A(x)$

Define the maximum value of the uniform distribution.

```R
f <- function(x){
  f <- exp(-x^2/2)*(1+cos(pi*x))
  return(f)
}

f_x_1 <- function(x){
  return(exp(-x^2/2))
}

f_x_2 <- function(x){
  return(1+cos(pi*x))
}

g_u_1 <- function(u){
  return(sqrt(-2*log(u)))
}

g_u_2<- function(u){
  g <- acos(u-1)/pi
  if(g>pi/2.0){
    g <- g-pi
  }
  return(g)
}
```

Generate the samples.

```R
# Set the generation rounds and initial value
times <- 5000
X_U <- data.frame(X=numeric(times),U1=numeric(times),U2=numeric(times))
X_U$X[0] <- 0

# Sampling Procedure
for(i in c(2:times)){
  X_U$U1[i] <- runif(1,min=0,max=f_x_1(X_U$X[i-1]))
  X_U$U2[i] <- runif(1,min=0,max=f_x_2(X_U$X[i-1]))
  X_U$X[i] <- runif(1,
                    min=max(c(-0.5,-g_u_1(X_U$U1[i]),-g_u_2(X_U$U2[i]))),
                    max=min(c(0.5,g_u_1(X_U$U1[i])),g_u_2(X_U$U2[i])))
}
```

Plot the result:

```R
x <- seq(-0.5,0.5,by=0.01)
C <- sum(f(x))*0.01
X_U$U_line <- f(X_U$X)/C
    
ggplot(data=X_U)+
  geom_density(aes(x=X),size=1,alpha=0.5,colour="blue")+
  geom_line(aes(x=X,y=U_line),size=1)
```

![](/img/in-post/Bayesian/plot3-1.png)