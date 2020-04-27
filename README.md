# ZipBomb

A zip bomb, also known as a zip of death or decompression bomb, is a malicious archive file designed to crash or render useless the program or system reading it.

This is a small script written in Python which generates such a zip bomb. It is based on [this repo](https://github.com/damianrusinek/zip-bomb) but allows you to specify depth and width when using the nested flavor.

## Usage
```Usage: zip-bomb.py [-D DEPTH] [-C COPIES] [-S SIZE] <mode> <out_zip_file>

Creates ZIP bomb archive

-S - for nested-size: decompression size in MB
-D - for nested-depth: nesting depth
-C - for nested-depth: copies per layer
<mode> - mode of compression
  nested-size - nested zip file driven by given size value
  nested-depth - nested zip file driven by given depth and width values, 1MB dummy
  flat   - flat file without nested zips
<out_zip_file> - path to destination file
```

## Sample Run - Flat mode 

`python zip-bomb.py -S 1024 flat out.zip`

### Output
```
Compressed File Size: 1020.36 KB
Size After Decompression: 1020 MB
Generation Time: 29.44s
```

## Sample Run - Nested size mode 

`python zip-bomb.py -S 1024 nested-size out.zip`

### Output
```
Warning: Using nested mode. Actual size may differ from given.
Compressed File Size: 1.81 KB
Size After Decompression: 1026 MB
Generation Time: 0.67s
```


## Sample Run - Nested depth mode

`python zip-bomb.py nested-depth -D 10 -C 2 out.zip`

### Output
```
Warning: Using nested mode. Actual size may differ from given.
Compressed File Size: 2.40 KB
Size After Decompression: 1024 MB
Generation Time: 0.08s
```