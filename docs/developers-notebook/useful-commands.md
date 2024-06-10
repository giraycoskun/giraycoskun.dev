# Useful Tools

List of useful tools and commands to remember.

## ImageMagick

<https://imagemagick.org/index.php>

``` zsh title="Convert HEIC to JPG in bulk"
magick mogrify -monitor -format jpg *.HEIC
```

## Git


## FFMPEG

```zsh
ffmpeg -protocol_whitelist file,http,https,tcp,tls,crypto -i index.m3u8 -c copy -bsf:a aac_adtstoasc index.mp4
```

```zsh
for i in *.mkv; do ffmpeg -i "$i" -c:a copy "${i%.*}.mp4"; done
```
