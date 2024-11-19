# clean-apple-books-epubs

Hello, i wrote a clean simple script. You don't have to download any complex/unknown softwares.

1. Extract all of your apple books epubs in a folder.

2. Open the folder in terminal app and run this script.


```
for f in *.epub; do if [ -d "$f" ]; then (cd "$f" && find . -name "iTunesMetadata*.plist" -delete 2>/dev/null && zip -0X "../tmp.epub" mimetype >/dev/null && zip -rDX9 "../tmp.epub" * -x "*.DS_Store" -x mimetype >/dev/null && echo "Converting: $f") && rm -rf "$f" && mv tmp.epub "$f"; elif [[ $(unzip -l "$f" 2>/dev/null | grep iTunesMetadata) == "" ]]; then echo "Already clean: $f"; else echo "Converting: $f"; fi; done
```

3. This will clean all the apple exported epub to clean epub files.
