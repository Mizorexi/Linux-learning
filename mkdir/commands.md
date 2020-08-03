 ### 创建目录 mkdir
mkdir -options -params

options:
1. -m 在创建目录的同时设置权限
           mkdir -m 700 test
2. -p 递归创建目录
         e.g.:  mkdir test 在当前目录下创建名为test的目录
                mkdir a b c 在当前目录下创建名为a b c三个目录
                mkdir -p a/b/c 创建多层目录.
3. 权限说明
linux一共有9个权限设定，三个用户级别owner,group,others.三种访问权限r(read)==4,w(write)==2,x(execute)==1,-表示未被授予权限.
          
输入 ls -l xxx.xxx （xxx.xxx是文件名）查看权限
````
drwxr-xr-x 2 mizore mizore 4096 Aug  2 22:02 Templates
drwxrwxr-x 2 mizore mizore 4096 Aug  2 22:41 test
````
开头为d表示文件夹,-表示为文件.
          
*使用pwd查看当前路径*

### 文件权限 chmod
chmod [options] mode files

mode(权限设定字符串):[ugoa...][[+-=][rwxX]...][,...]
1. u代表owner,g代表group,o表示others,a表示all(所有用户)(默认)
2. +表示增加权限,-表示取消权限,=表示唯一设定权限
3. r=read,w=write,x=execute,X 表示只有当该文件是个子目录或者该文件已经被设定过为可执行。

可以使用数字表示用户权限,如:chmod 7(4+2+1)77 test 表示给test三种用户都赋予全部权限,可以设置第四位,位于最前面,可取4,2,1:
1. 为4时表示执行时设置用户ID，用于授权给基于文件属主的进程，而不是给创建此进程的用户
2. 为2时表示执行时设置用户组ID，用于授权给基于文件所在组的进程，而不是基于创建此进程的用户
3. 为1时表示设置粘着位
