# ijkplayer-ios
编译ijkplayer流程

下载安装流程参考： https://github.com/bilibili/ijkplayer

支持https
1，修改 config/module-lite-hevc.sh 文件，新增 export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-openssl"

2，运行 ./init-ios-openssl.sh，运行 ./init-ios/sh （如果报错找不到相关架构，进入文件删除即可）

3，cd ios/，依次运行 ./compile-ffmpeg.sh clean， ./compile-openssl.sh arm64(指定架构或者all)， ./compile-ffmpeg.sh arm64(指定架构或者all)   （如果报错找不到相关架构，进入文件删除即可）

4，打开IJKMediaPlayer项目，加入ios/build/universal/lib中 libcrypto.a 和 libssl.a 库 （这步是关键）

5，编译完成即可支持https （编译遇到无法支持的架构可添加自定义架构参数 VALID_ARCHS）



新增支持音视频类型，在 config/module-lite.sh 文件中增加指令后重复上述编译流程即可

export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=ape"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=vorbis"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16be"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16be_planar"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16le"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16le_planar"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=mpeg4"    #支持mpeg4

export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-demuxer=amr"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-demuxer=ogg"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-demuxer=ape"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-demuxer=wav"  #支持wav

export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-parser=vorbis"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-parser=opus"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-parser=cook"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-parser=ac3"
export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-parser=mpegaudio"

