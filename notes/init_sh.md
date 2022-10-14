- `init.sh`做了什么
    - 输出信息：
    ```
    ysyx-workbench (ysyx2204) » bash init.sh nemu                      songmuhan@lenovo
    Cloning into 'nemu'...
    remote: Enumerating objects: 1561, done.
    remote: Counting objects: 100% (428/428), done.
    remote: Compressing objects: 100% (233/233), done.
    remote: Total 1561 (delta 244), reused 255 (delta 188), pack-reused 1133
    Receiving objects: 100% (1561/1561), 403.20 KiB | 461.00 KiB/s, done.
    Resolving deltas: 100% (761/761), done.
    [ysyx2204 77fd37d] NJU-ProjectN/nemu ysyx2204 initialized
    131 files changed, 19203 insertions(+)
    create mode 100644 nemu/.gitignore
    create mode 100644 nemu/Kconfig
    create mode 100644 nemu/Makefile
    ....
    By default this script will add environment variables into ~/.bashrc.
    After that, please run 'source ~/.bashrc' to let these variables take effect.
    If you use shell other than bash, please add these environment variables manually.
    ```

    - 一共有2个步骤。 1） git clone nemu 2) 添加环境变量到~/.bashrc.
    - 查看~/.bashrc, 发现最后有一行`export NEMU_HOME=/home/songmuhan/ysyx-workbench/nemu`, 即设置NEMU_HOME为对应的directory
    - `bash init.sh abstract-machine`同理，多clone了一个`fceux-am`。
  
- RTFSC: `init.sh`
   - `bash init.sh nemu`中`nemu`会传递给变量`$1`
   - 然后通过`init NJU-ProjectN/nemu ysyx2204 nemu true NEMU_HOME`调用`function init()`
     - `usage: init repo branch directory trace [env]`中 `repo`就是`$1`
     - 检查是否存在nemu的directory，如果不存在，就clone一个
     - 如果trace为true，就git commit一个initilizatin
     - 如果有`env`，就调用`function addenv()`,把`env`设置成`directory` 
    
