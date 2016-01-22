# Zsh and Oh my Zsh

  [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-ohmyzsh-blue.svg)](https://galaxy.ansible.com/list#/roles/6323)

  Installs and configures zsh and oh-my-zsh plugin.

  This role it is compatible with Debian/Ubuntu.

  We provide a cascade of config files to allow you to set your custom settings and install your desired plugins without
  hassle.

  With this role you can install a custom zsh settings and plugins in your remote server or local machine, for a given
  list of selected users using `ohmyzsh_users` variable (even root). The config is shared between all users, but
  customized settings for a single user is allowed if you want.

  If you need to overwrite any setting that concerns to `zsh` you should place your config in `~/.zsh/conf.d` directory.
  Also, your custom aliases should be placed in `~/.zsh/aliases.local` file


## Requirements

  Ansible  1.9 or greater

## Role Variables

### `users_list`

  A list of users to install zsh and oh-my-zsh. Users myst exists beforehand.
  ```yaml
  ohmyzsh_users:
    - name: mmacia                # Required.
      state: present              # present or absent. Use absent to return to bash shell.
      theme: robbyrussell         # Preferred theme to use. This variable overrides `ohmyzsh_default_theme`
      ssh_ids:                    # List of SSH ids to add to ohmyzsh ssh manager plugin
        - id_work                 #   refer to [documentation](https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/ssh-agent/ssh-agent.plugin.zsh) for examples
        - id_personal
      plugins:                    # Use this variable to enable a custom list of plugins
        - rails                   # Note that this variable adds plugins to those defined in `ohmyzsh_default_plugins`
        - git
  ```

### `ohmyzsh_default_theme`

  Default theme to use.

### `ohmyzsh_default_plugins`

  Defaul list of oh-my-zsh plugins to enable.

## Dependencies

  None.

## License

  MIT

## Author Information

  Moisés Maciá <mmacia@gmail.com>
