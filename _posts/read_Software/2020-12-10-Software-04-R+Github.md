---
title: "「Software」4 R language/Github"
subtitle: "R language/Github - Some Basic Tips"
layout: post
author: "Linsui"
header-style: text
tags:
  - R language  
  - 笔记

---

# R

## Tips

- melt data, create several copies:

  ```R
  library(reshape)
  mdata <- melt(mydata, id=c("id","time"))
  ```

  - Here, `id` and `time` are maintained, other variables represents the value but for different objects.

  - A simple example is:

    The original table:

    | id   | TIME | X1   | x2   |
    | ---- | ---- | ---- | ---- |
    | 1    | 1    | 3    | 2    |

    The transformed table:

    | ID   | TIME | Variable | Value |
    | ---- | ---- | -------- | ----- |
    | 1    | 1    | X1       | 3     |
    | 1    | 1    | X2       | 2     |
    |      |      |          |       |

- facet plot

  ```R
  p <- ggplot(data = Full_result, mapping = aes(x = carat, y = variable))+
    geom_boxplot()+
    facet_grid('p+exchange ~ rho')
  ```

  - `p+exhange` is the row split method
  - `rho` is the column split method

# Github

## Tips

- Deploy github authority on Linux:

  - Create `ssh` folder:

    ```cmd
    mkdir ~/.ssh
    ```

  - Generate and copy the ssh key:

    ```cmd
    ssh-keygen -t rsa -C "email_name@email_server.com"
    ```

    ```cmd
     cat id_rsa.pub
    ```

  - Log in github.com -> `Setting` -> `SSH and GPG keys`

    - `New SSH keys` 
    - paste ssh key you generated

  - Add config

    ```cmd
    git config --global user.name "name" 
    ```

    