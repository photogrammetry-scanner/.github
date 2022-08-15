Crop, scale, increse speed
```
ffmpeg -i input_video.mp4 -filter:v "crop=in_w-600:in_h-10, scale=720:-1, setpts=0.1*PTS" output.mp4
```

Create palette, compress to gif, compress gif:
```
ffmpeg -i input_video.mp4 -filter_complex "[0:v] palettegen" palette.png
ffmpeg -i input_video.mp4 -i palette.png -filter_complex "[0:v] fps=10,scale=320:-1 [new];[new][1:v] paletteuse" output.gif
gifsicle -O3 --lossy=100 output.gif -o compressed.gif
```
