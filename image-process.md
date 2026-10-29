# Image processing

## Find JPGs that have a HEIC with the same name
Lists only; deletes nothing. Matches by path without extension, case-insensitive on the extension, so `a/IMG_1.HEIC` pairs with `a/IMG_1.jpg` but not with `b/IMG_1.jpg`.
```sh
find . -type f -iname '*.heic' | while IFS= read -r h; do
  b=${h%.*}
  for j in "$b".[jJ][pP][gG]; do [ -e "$j" ] && printf '%s\n' "$j"; done
done
```
To delete what it lists, pipe through `tr '\n' '\0' | xargs -0 rm --` after checking the output. Filenames containing newlines are not handled.
