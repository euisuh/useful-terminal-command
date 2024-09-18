# Image Process
Terminal command related to image processing


## Removing `JPG` duplicates derived from `HEIC`
```shell
find . -type f \( -iname '*.jpg' -o -iname '*.heic' \) | \
awk -F'[./]' '{ 
    base = tolower($(NF-1)); 
    ext = tolower($NF); 
    if (ext == "jpg") {
        jpg_files[base] = $0;
    } else if (ext == "heic") {
        heic_files[base] = $0;
    }
} 
END { 
    duplicates = 0; 
    for (base in jpg_files) { 
        if (base in heic_files) { 
            duplicates++; 
            print "Duplicate found and deleting JPG:";
            print jpg_files[base];
            print heic_files[base];
            print "-----";
            # Delete the jpg file
            system("rm \"" jpg_files[base] "\"");
        } 
    } 
    print "Number of duplicates found and JPGs deleted:", duplicates; 
}'
```
