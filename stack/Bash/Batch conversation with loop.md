---
Owner: Sharafat Karim
Last edited time: 2023-01-03T18:37
---
```Bash
for i in .mp4; do ffmpeg -i "$i" "${i%.}".gif; done
```

we can loop through file is  
  
`for i in *`

loop through mp4  
  
`for i in *.mp4`

loop through folder  
  
`for i in */`

  

Another example from Afnan Sami,

```Bash
for i in *.png; do ffmpeg -i "$i" "${i%.*}.webp"; done
```

### Image to AVIF with imagemagick

```Bash
for i in *; do magick "$i" "${i%.*}".avif; done
```

```Bash
for i in *; do magick "$i" "${i::-4}.avif"; done
```

credit - Fazle Rabbi bro