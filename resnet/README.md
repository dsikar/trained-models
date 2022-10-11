# Packing and unpacking trained models 
Used a RESNET trained model over 25MB (github maximum allowed file size, could have used LFS but did not do it this time).
Following [these instructions](https://unix.stackexchange.com/questions/61774/create-a-tar-archive-split-into-blocks-of-a-maximum-size).

To split the file:
```
tar cvzf - resnet101-imagenet.pth | split -b 25m - resnet.tar.gz.
```

To patch them back together:
```
cat resnet.tar.gz.a* | tar xzvf -
```
