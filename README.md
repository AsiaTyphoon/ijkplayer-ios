# ijkplayer-ios
编译ijkplayer流程

下载安装流程参考： https://github.com/bilibili/ijkplayer

支持https
1，修改 config/module-lite-hevc.sh 文件，新增 export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-openssl"
2，运行 ./init-ios-openssl.sh，运行 ./init-ios/sh （如果报错找不到相关架构，进入文件删除即可）
3，cd ios/，依次运行 ./compile-ffmpeg.sh clean， ./compile-openssl.sh arm64(指定架构或者all)， ./compile-ffmpeg.sh arm64(指定架构或者all)   （如果报错找不到相关架构，进入文件删除即可）
4，打开IJKMediaPlayer项目，加入ios/build/universal/lib中 libcrypto.a 和 libssl.a 库 （这步是关键）
5，编译完成即可支持https （编译遇到无法支持的架构可添加自定义架构参数 VALID_ARCHS）






