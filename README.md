
for f in "$@"
do
    xattr -d com.apple.quarantine "$f" 2>/dev/null
done
