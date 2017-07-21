# ga-proxy

[![GitHub release](https://img.shields.io/github/release/giuem/ga-proxy.svg?style=flat-square)](https://github.com/giuem/ga-proxy/releases/latest)

Speed up Google Analytics



## Get Start

### 1. Install 

Download binary from [release](https://github.com/giuem/ga-proxy/releases) or build yourself.

### 2. Run

```
./ga_proxy [arguments]
```

options:

```
-d, -debug output debug info.
-s, -skip_ssl skip ssl verify. (some envirinment don't have certificate)
-l, -listen listen address, default is :80
```

e.g.

```
./ga_proxy -s -l :4000
```

The program will run at 0.0.0.0:4000 and skip SSL verify 

### 3. Add Script to your website

See [script](script.js).

Here is compression version.

```javascript
!function(a,b,c,d,e){var f=c.screen,g=encodeURIComponent,h=["ga="+a,"dt="+g(d.title),"dr="+g(d.referrer),"ul="+(e.language||e.browserLanguage||e.userLanguage),"sd="+f.colorDepth+"-bit","sr="+f.width+"x"+f.height,"vp="+Math.max(d.documentElement.clientWidth,c.innerWidth||0)+"x"+Math.max(d.documentElement.clientHeight,c.innerHeight||0),"z="+ +new Date];c.__ga_img=new Image,c.__ga_img.src=b+"?"+h.join("&")}("UA-xxxx-x","https://ga.giuem.com",window,document,navigator,location);
```

You need to change `UA-xxxx-x` and `https://ga.giuem.com` to your own.

Or simple usage, just change `UA-xxxx-x`, and use my service (not fast outside of China)

## Build

1. Get requirement

   ```bash
   go get github.com/mitchellh/gox github.com/tomasen/realip github.com/satori/go.uuid 
   ```


2. Build

   ```bash
   gox -os="!freebsd !netbsd !openbsd" -ldflags="-s -w" -output="build/{{.Dir}}_{{.OS}}_{{.Arch}}"
   ```
