# INSTALL FFMPEG ON MACOS

https://phoenixnap.com/kb/ffmpeg-mac

```
brew update
brew upgrade
brew install ffmpeg --HEAD
ffmpeg
```

# CONVERT VIDEO

### Convert all files in directory

```
for f in *.mp4; do ffmpeg -i "${f}" "${f%%.*}.mkv"; done
```

# Concat all files in directory 
```
find *.mkv | sed 's:\ :\\\ :g'| sed 's/^/file /' > fl.txt; ffmpeg -f concat -i fl.txt -vcodec copy ./output/final.mp4; rm fl.txt
```

# YOUTUBE

### Translate Video to other languages
Description available by [link](https://github.com/ilyhalight/voice-over-translation?tab=readme-ov-file)