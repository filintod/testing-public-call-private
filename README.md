# Runing in grid

### Add your ssh key to config.yml file

```
# substitute the key here
git_ssh="${YOUR_SSH_KEY_ENV_VAR_OR_CAT_THE_KEY_FILE}"

# convert to single line to avoid issues with multiline in dockerfile
git_ssh_no_space=$(echo $git_ssh | sed -z 's/ *\n//g')

# config file above is saved in a file config.yml
sed -i "s#__ssh_key__#${git_ssh_no_space}#" config.yml
```

__Note__: do not commit the config.yml file after executing or you'll be storing the ssh key in your repository!!

### Execute in Grid

```
grid run --config config.yml hello.py
```
