```bash
# Print the size and absolute path of the files recursively
for filename in $(find . -type f -print); do du -s "$filename"; done
```

```bash
#!/bin/bash
#
# Print immediate parent directory along with filename and the file size
for filename in $(find . -type f -print)
    do
        du_out=$(du -s $filename)
        splitted=($(echo ${du_out}))
        size="${splitted[0]}"
        abs_path="${splitted[1]}"
        parent_dir=$(basename $(dirname "$abs_path"))
        filename=$(basename "$abs_path")
        echo "${parent_dir},${filename},${size}"
    done
```

```bash
# Print the filename, compressed size, compression factor and ZIP archive name of all the zipped files in a directory
for file in $(find . -type f -print); do zipinfo -m "$file" | awk -v filename="$file" -F ' ' '{ print $4, "\t", $6, "\t", $10, "\t", filename }'; done;
```
