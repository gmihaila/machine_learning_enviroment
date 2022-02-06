# Apple M1 Various Software Issue Fixes

Here I post fixes to various install packages specific to MacBooks with the new M1 chip. Since I personally own one and have this problems I will start posting them here.

I plan to avoid HomeBrew or other package managers for Mac. While these tools are very beneficial, I like to to go the hard path and install things on my own and
learn more things along the way.

I'm also not interested in installing anything outside of my home directory. From my previous experience working on a HPC cluster, I always build from source locally
and avoid running any sudo commands. Because of this I created a src folder under my home directory where I will install all my software.

## Matplotlib

In order to install Matplotlib on the new Apple M1 macs you need to follow some extra steps as mentioned in [this solution](https://stackoverflow.com/a/66456204)
For this I will need to install libjpeg from source (instead of using HomeBrew).

### Install libjpeg from source

I created a folder under my home directory `/Users/my_user/src/libjpeg`. 
Inside this folder I run the following commands to download the source code and install it:

```bash
curl http://www.ijg.org/files/jpegsrc.v9e.tar.gz -o jpegsrc.v9e.tar.gz
gunzip jpegsrc.v9e.tar.gz
tar -xvf jpegsrc.v9e.tar
cd jpeg-9e
./configure --prefix=/Users/my_user/src/libjpeg
make
make test
make install
```

Keep folder clean but keep the .tar file in case I need to re-compile this in the future:

```bash
cd ..
rm -rf jpeg-9e 
```

Now we need to add our binaries to path. We can use `sudo vim /etc/paths` to make it available across all users.

Again, to avoid using sudo and doing everything local I will go with my current user 
