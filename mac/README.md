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

- 设置代理

  - > 修改仓库配置文件：偏好设置 -> Git -> 编辑配置文件，添加 
    >
    > ```
    > [http]
    > 	proxy = your_proxy
    > [https]
    > 	proxy = your_proxy
    > ```
    >
    > 也可以只修改某个仓库的配置文件，打开某个仓库 -> 仓库 -> 仓库设置 -> 高级 -> 修改配置文件