This batch renames filename pfjorljntvczthbsuvwgmnsdfg.md to filename.md

for f in *.md; do 
  new=$(echo "$f" | sed -E 's/ [0-9a-fA-F]{32}\.md$/.md/')
  [ "$f" != "$new" ] && mv -n "$f" "$new"
done
