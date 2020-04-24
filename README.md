# geek-bash/fish

## bash
* Bash config file:  
    `~/.bashrc`

## fish

* Install `fish`  
    * Ubuntu or Debian:  
    `$ sudo apt-get install fish`
    * Mac:  
    `$ brew install fish`

* Fish config file:  
    * From file:  
    `~/.config/fish/config.fish`
    * From web:  
    `$ fish_config`

* In stall `Oh My Fish`
    ```
    # with git
    $ git clone https://github.com/oh-my-fish/oh-my-fish
    $ cd oh-my-fish
    $ bin/install --offline
    # with a tarball
    $ curl -L https://get.oh-my.fish > install
    $ fish install --offline=omf.tar.gz
    ```
* Fish grammar

    * if语句。 
        ```
        if grep fish /etc/shells
            echo Found fish
        else if grep bash /etc/shells
            echo Found bash
        else
            echo Got nothing
        end
        ```

    * switch语句。
        ```
        switch (uname)
        case Linux
            echo Hi Tux!
        case Darwin
            echo Hi Hexley!
        case FreeBSD NetBSD DragonFly
            echo Hi Beastie!
        case '*'
            echo Hi, stranger!
        end
        ```
    
    * while循环。 

        ```
        while true
            echo "Loop forever"
        end
        ```
        
    * for循环。
        ```
        for file in *.txt
            cp $file $file.bak
        end
        ```

    * 函数  
        Fish 的函数用来封装命令，或者为现有的命令起别名。
        ```
        function ll
            ls -lhG $argv
        end
        ```
        上面代码定义了一个ll函数。命令行执行这个函数以后，就可以用ll命令替代ls -lhG。其中，变量$argv表示函数的参数。


        ```
        function ls
            command ls -hG $argv
        end
        ```
        上面的代码重新定义ls命令。注意，函数体内的ls之前，要加上command，否则会因为无限循环而报错。

    * 提示符  
        fish_prompt函数用于定义命令行提示符（prompt）。
        ```
        function fish_prompt
            set_color purple
            date "+%m/%d/%y"
            set_color FF0
            echo (pwd) '>'
            set_color normal
        end
        ```
        执行上面的函数以后，你的命令行提示符就会变成下面这样。
        ```
        02/06/13
        /home/tutorial > 
        ```

