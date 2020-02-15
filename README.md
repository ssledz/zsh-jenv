# Installation

Plugin assumes that [jenv](https://www.jenv.be/) is installed either in `~/.jenv` or `/usr/local/jenv`

## Oh My Zsh

1. Clone this repository into `$ZSH_CUSTOM/plugins` (by default `~/.oh-my-zsh/custom/plugins`)

    ```sh
    git clone https://github.com/ssledz/zsh-jenv ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-jenv
    ```

2. Add the plugin to the list of plugins for Oh My Zsh to load (inside `~/.zshrc`):

    ```sh
    plugins=(zsh-jenv)
    ```

3. Start a new terminal session.

## Usage

## Setting prompt

```
local ret_status="%(?:%{$fg_bold[green]%}➜ :%{$fg_bold[red]%}➜ )"
PROMPT='${ret_status} %{$fg[cyan]%}%c%{$reset_color%} $(jenv_prompt_info)'
```

```
➜  zsh-jenv java:(1.8)
```

## zsh-jenv helper functions

gc logs on

```
$ jenv shell-options
jenv: no shell-specific options configured
$ gc_set
$ jenv shell-options
 -XX:+PrintGCDetails -Xloggc:gc.log
```

debug on

```
$ jdebug_set
$ jenv shell-options
 -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n
```

jrebel on

```
$ jrebel_set
$ jenv shell-options
 -javaagent:/home/ssledz/bin/jrebel/jrebel.jar -noverify
```

jprofiler on

```
$ jprofiler_set
$ jenv shell-options
 -javaagent:/home/ssledz/bin/jprofiler/bin/agent.jar
```

jboss debug on

```
$ jboss_debug_set
$ jenv shell-options
 -Xrunjdwp:server=y,transport=dt_socket,address=8787,suspend=n
```

hotswap on

```
$ hotswap_set
$ jenv shell-options
 -XXaltjvm=dcevm -javaagent:/home/ssledz/bin/hotswap/hotswap-agent.jar=autoHotswap=true
```

There is also counter options for unseting shell options like

```
jdebug_unset
gc_unset
jrebel_unset
jprofiler_unset
jboss_debug_unset
hotswap_unset
```
