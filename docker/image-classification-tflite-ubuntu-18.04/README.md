## Ubuntu 18.04

**NB:** `#` means execution under root or with `sudo`.

### Build image
```
# docker build . -f Dockerfile -t image-classification-tflite-ubuntu-18.04
```

### Check image 
#### View layer-by-layer build history
```
# docker history image-classification-tflite-ubuntu-18.04
```
#### View space usage
```
# docker system df -v
```

### Run image

#### Image Classification (default)
```
# docker run --rm image-classification-tflite-ubuntu-18.04
```
**NB:** Equivalent to:
```
# docker run --rm image-classification-tflite-ubuntu-18.04 \
ck run program:image-classification-tflite
```

#### Image Classification (custom)
```
# docker run --rm image-classification-tflite-ubuntu-18.04 \
ck run program:image-classification-tflite --env.CK_BATCH_COUNT=10
```

#### Shell (needs changing Dockerfile)
To allow running shell, in `Dockerfile` change:
```
ENTRYPOINT ["/bin/bash"]
CMD ["ck run program:image-classification-tflite"]
```
to:
```
ENTRYPOINT ["/bin/bash", "-c"]
CMD ["ck run program:image-classification-tflite"]
```
and run as:
```
# docker run -it --rm image-classification-tflite-ubuntu-18.04 bash
```