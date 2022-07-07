# Runing in grid

```
# substitute the key here
git_ssh="${YOUR_SSH_KEY_ENV_VAR_OR_CAT_THE_KEY_FILE}"

# convert to single line to avoid issues with multiline in dockerfile
git_ssh_no_space=$(echo $git_ssh | sed -z 's/ *\n//g')

# config file above is saved in a file config.yml
sed -i "s#__ssh_key__#${git_ssh_no_space}#" config.yml

grid run --config config.yml --instance_type g4dn.xlarge hello.py
```
