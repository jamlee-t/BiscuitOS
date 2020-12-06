# Biscuitos 测试
## 清理掉所有生成文件
```
make mrproper && make clean && rm -fr output
```

## 生成的过程
生成的过程分为两步：
1. 生成 .config 文件 和 include 目录。include/config/auto.conf 里生成的配置变量，是可以被 Makefile 引入的
2. 根据 include/config/auto.conf 的配置引入不同的Makefile，SUBTARGET被这些不同的Makefile改变。默认 target 是all ， all 依赖 SUBTARGET 定义的内容，所以会生成不同的操作系统。
```
因为引入了 auto.conf, 根据 auto.conf 的内容， include 下面不同 makefile
引入 toolchain/Makefile
引入 package/Makefile
引入 board/Makefile
引入 kernel/linux/Makefile
引入 fs/Makefile
```