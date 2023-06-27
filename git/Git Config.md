# Sections

## Links

## Reset Config Script

## Knowledge

 ### Git Configuration: System, Global and Local Configurations
+ Git stores configuration variables in 3 locations **System**, **Global**, and **Local** . These 3 differ from each other in where the config files are stored but more importantly the **scope that they handle**.

### System
> Stored in [path]/etc/gitconfig file

```zsh
git config --system
```


### Global
> Stored in ~/.gitconfig or in ~/.config/git/config


```zsh
git config --global
```

### Local
> stored in the /.git file of the file that you are currently using 


```zsh
git config --local
```
	