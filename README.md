ijkplayer
=========
- Video player based on [ffplay](http://ffmpeg.org)
 - Android: [MediaPlayer-like](android/ijkmediaplayer/src/tv/danmaku/ijk/media/player/AbstractMediaPlayer.java)
 - iOS: [MediaPlayer.framework-like](ios/IJKMediaPlayer/IJKMediaPlayer/IJKMediaPlayback.h)

### My Build Enviroment
- Common
 - Mac OS X 10.9.4
- Android
 - [ADT v22.6.2-1085508](http://developer.android.com/sdk/index.html)
 - [NDK r9d](http://developer.android.com/tools/sdk/ndk/index.html)
- iOS
 - Xcode 6.0.1
- [HomeBrew](http://brew.sh)
 - ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
 - brew install git

### Latest Changes
- [NEWS.md](NEWS.md)

### Features
- Common
 - remove rarely used ffmpeg components to reduce binary size [config/module-lite.sh](config/module-lite.sh)
 - workaround for some buggy online video.
- Android
 - platform: API 9~19
 - cpu: ARMv7a, x86, ARMv5 (not tested on real devices)
 - api: [MediaPlayer-like](android/ijkmediaplayer/src/tv/danmaku/ijk/media/player/IMediaPlayer.java)
 - video output: NativeWindow
 - audio output: AudioTrack
- iOS
 - platform: iOS 5.1.1~8.0.x
 - cpu: ARMv7, ARMv7s, ARM64, i386, x86_64
 - api: [MediaPlayer.framework-like](ios/IJKMediaPlayer/IJKMediaPlayer/IJKMediaPlayback.h)
 - video-output: OpenGL ES 2.0 (I420/YV12 shaders)
 - audio-output: AudioQueue, AudioUnit

### TODO
- Android
 - hw-accelerator: HW decode
- iOS
 - api: AVFoundation-like
 - hw-accelerator: HW decode

### NOT-ON-PLAN
- obsolete platforms (Android: API-8 and below; iOS: below 5.1.1)
- obsolete cpu: ARMv5, ARMv6, MIPS (I don't even have these types of devices…)
- native subtitle render

### Before Build
- If you prefer more codec/format
```
ln -fs config/module-default.sh config/module.sh
```

- If you prefer less codec/format for smaller binary size (by default)
```
ln -fs config/module-lite.sh config/module.sh
```

- If you'd like to share your config, pull request is welcome.

### Build Android
- Latest tag

```
git clone https://github.com/bbcallen/ijkplayer.git ijkplayer-android-stable
cd ijkplayer-android-stable
git checkout -B latest n0.1.3

./init-android.sh

cd android
./compile-ffmpeg.sh
./compile-ijk.sh

# import android/ijkmediaplayer for MediaPlayer-like interface (recommended)
# import android/ijkmediawidget for VideoView-like interface (based on Vitamio UI)
# import android/ijkmediademo for VideoActivity demo (Simple VideoActivity)
```

- Unstable

```
git clone https://github.com/bbcallen/ijkplayer.git ijkplayer-android-master
cd ijkplayer-android-master
git checkout master

./init-android.sh

cd android
./compile-ffmpeg.sh
./compile-ijk.sh

# or Add Native Support in eclipse
# cd ijkmediaplayer
# cp .cproject.bak .cproject

# import android/ijkmediaplayer for MediaPlayer-like interface (recommended)
# import android/ijkmediawidget for VideoView-like interface (based on Vitamio UI)
# import android/ijkmediademo for VideoActivity demo (Simple VideoActivity)
```

### Build iOS
- Latest tag

```
git clone https://github.com/bbcallen/ijkplayer.git ijkplayer-ios-stable
cd ijkplayer-ios-stable
git checkout -B latest n0.1.3

./init-ios.sh

cd ios
./compile-ffmpeg.sh all

# import ios/IJKMediaPlayer for MediaPlayer.framework-like interface (recommended)
# open ios/IJKMediaDemo/IJKMediaDemo.xcodeproj with Xcode
```

- Unstable

```
git clone https://github.com/bbcallen/ijkplayer.git ijkplayer-ios-master
cd ijkplayer-ios-master
git checkout master

./init-ios.sh

cd ios
./compile-ffmpeg.sh all

# import ios/IJKMediaPlayer for MediaPlayer.framework-like interface (recommended)
# open ios/IJKMediaDemo/IJKMediaDemo.xcodeproj with Xcode
```

### Links
- [FFmpeg_b4a](http://www.basic4ppc.com/android/forum/threads/ffmpeg_b4a-a-ffmpeg-library-for-b4a-decoding-streaming.44476/)
- 中文
 - [ijkplayer学习系列之环境搭建 2013-11-23](http://blog.csdn.net/nfer_zhuang/article/details/16905755)
 - [Ubuntu 14.04 下编译 ijkplayer Android 2014-08-01](http://xqq.0ginr.com/ijkplayer-build/#more-134)

### License

```
Copyright (C) 2013-2014 Zhang Rui <bbcallen@gmail.com> 
Licensed under LGPLv2.1 or later
```

ijkplayer is based on or derives from projects below:
- LGPL
  - [FFmpeg](http://git.videolan.org/?p=ffmpeg.git)
  - [libVLC](http://git.videolan.org/?p=vlc.git)
  - [kxmovie](https://github.com/kolyvan/kxmovie)
- zlib license
  - [SDL](http://www.libsdl.org)
- Apache License v2
  - [VitamioBundle](https://github.com/yixia/VitamioBundle)
- BSD-style license
  - [libyuv](https://code.google.com/p/libyuv/)
- ISC license
  - [libyuv/source/x86inc.asm](https://code.google.com/p/libyuv/source/browse/trunk/source/x86inc.asm)

ijkplayer's build scripts are based on or derives from projects below:
- [gas-preprocessor](http://git.libav.org/?p=gas-preprocessor.git)
- [VideoLAN](http://git.videolan.org)
- [yixia/FFmpeg-Android](https://github.com/yixia/FFmpeg-Android)
- [kewlbear/FFmpeg-iOS-build-script](http://github.com/kewlbear/FFmpeg-iOS-build-script) 

### Commercial Use
ijkplayer is licensed under LGPLv2.1 or later, so itself is free for commercial use under LGPLv2.1 or later

But ijkplayer is also based on other different projects under various licenses, which I have no idea whether they are compatible to each other or to your product.

[IANAL](http://en.wikipedia.org/wiki/IANAL), you should always ask your lawyer for these stuffs before use it in your product.
