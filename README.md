# CONVERT VIDEO

### Convert all files in directory

```
for f in *.mp4; do ffmpeg -i "${f}" "${f%%.*}.mkv"; done
```

# Concat all files in directory 
```
find *.mkv | sed 's:\ :\\\ :g'| sed 's/^/file /' > fl.txt; ffmpeg -f concat -i fl.txt -vcodec copy ./output/final.mp4; rm fl.txt
```