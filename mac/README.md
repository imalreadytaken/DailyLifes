# 安装

### Iterm2 

### Dash

### Typora

### zsh + oh-my-zsh

###### zsh

- 安装

  ```shell
  brew install zsh zsh-completions
  chsh -s /bin/zsh
  ```

###### Oh-my-zsh

- 安装

  ```shell
  git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
  cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
  ```


- 修改主题：.zshrc文件

  ```reStructuredText
  ZSH_THEME="random"
  ```

- 主题

  [主题列表]: https://github.com/robbyrussell/oh-my-zsh/wiki/themes

- 修改插件：.zshrc文件

  ```
  plugins=(
    git
    bundler
    dotenv
    osx
    rake
    rbenv
    ruby
  )
  ```



###### Powerline 字体

- 为了使用agnoster主题，需要安装该字体

    ```shell
    git clone https://github.com/powerline/fonts.git --depth=1
    cd fonts
    ./install.sh
    ```

###### 其它设置

- 命令行另起一行
  - *.zsh-theme中，修改PROMPT=''中的内容

### SourceTree

> 第一次修改用户名和邮箱信息失败了