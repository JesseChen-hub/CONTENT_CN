# GITHUB之mac电脑设置SSH

本文撰写时间是2022年9月22日。

## 查看电脑中是否有存在的SSH keys

* 打开Terminal输入以下指令

~~~
ls -al ~/.ssh
~~~

如果有类似以下的文件名，说明你电脑中已经有以前设置过的SSH keys - 当然如果没有的话，我们需要去重新创建。

    * id_rsa.pub
    * id_ecdsa.pub
    * id_ed25519.pub

假设我们电脑中已经有了SSH key。


## 创建一个SSH KEY

* 在terminal中执行以下命令,其中email的地址换成你Github的email地址

~~~
ssh-keygen -t ed25519 -C "your_email@example.com"
~~~

* 执行后会有一条提示问你产生的key放在哪个文件，不用管直接回车就行。（注意，如果你是设置多个ssh key，则需要不同的文件去储存，教程在[这里](https://betterprogramming.pub/how-to-set-up-multiple-ssh-keys-ae6688f76570))

* 然后是让你设置key的密码，直接回车就是不要密码。



## 把SSH KEY加入到 ssh-agent

* 打开Terminal，输入以下指令启动ssh-agent

~~~
eval "$(ssh-agent -s)"
~~~

* 如果是MacOS用户并且版本比Sierra 10.12.2更新，则还需要去编辑`~/.ssh/`中的`config`文件。执行以下命令打开该文件

~~~
open ~/.ssh/config
~~~

* 如果该文件不存在，则执行以下命令创建一个，然后再打开

~~~
touch ~/.ssh/config
#创建一个config文件
open ~/.ssh/config
#打开config文件
~~~

* 打开文件后，在文件放入以下内容。注意，如果你的SSH key文件(上面第一步有提到)名字和路径不是`~/.ssh/id_ed25519`,则把那里改成对应的你的key文件的名字和路径。

~~~
Host *
  AddKeysToAgent yes
  UseKeychain yes
  #如果你不想给key再单独设置一个密码的话，把UseKeychain这一行删掉
  IdentityFile ~/.ssh/id_ed25519
~~~

* 执行以下命令，把SSH key加入ssh-agent。同样，如果你的文件名字和路径和示例不一致，则需要对应修改

~~~
ssh-add -K ~/.ssh/id_ed25519
#如果在上一步没有设置ssh密码，则不需要-K这个选项
~~~

## 把SSH KEY添加到Github当中

* 复制`~/.ssh/id_ed25519.pub`这个文件内容，复制方法是以下命令

~~~
pbcopy < ~/.ssh/id_ed25519.pub
~~~

* 然后来到github的页面，settings -> SSH -> NEW

* 粘贴保存

这样就设置好了SSH KEY。
