# Snapdroid Legacy

Snapcast control client and player for Android.

Modified to work on at least Android 2.3.3 (API level 10).

You can download the APK from [releases](https://github.com/konradmb/snapdroid-legacy/releases/latest).


## Building Snapclient NDK lib

- Download and unpack Android NDK version r14b

- Run inside extracted NDK: \
`build/tools/make_standalone_toolchain.py --arch arm --api 9 --install-dir /dev/shm/my-android-toolchain --stl libc++`

- Download boost_1_74_0 and unpack to /dev/shm/my-android-toolchain

- Clone snapcast: \
  `git clone https://github.com/badaix/snapcast.git`

- Apply patch:
  ```
  cd snapcast
  git apply ../snapcast.patch
  ```

- `cd snapcast/externals/`

- `make NDK_DIR=/dev/shm/my-android-toolchain/ ARCH=arm`

- `cd ../client/`

- `make TARGET=ANDROID NDK_DIR=/dev/shm/my-android-toolchain/ ARCH=arm -j4`

- `/dev/shm/my-android-toolchain/bin/arm-linux-androideabi-strip ./snapclient`

- `cp snapclient ../../Snapcast/src/main/jniLibs/armeabi/libsnapclient.so`
  
## Building Snapdroid

- Build with Android Studio as usual.