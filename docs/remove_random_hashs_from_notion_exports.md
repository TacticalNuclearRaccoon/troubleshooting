stupid Notion (which is nothing else than a consipiracy against intelligent life and an extension to the brainless machinations of my boss) places a random hash at the end of expoted filenames because otherwise life is too enjoyable I guess...

What I want: remove the stupid hash so that
`DevOps 2abefdfbd243801c989ad47650268149.md
Sortir des silos 715f666f961847d4893cd4b066626f39.md
`
becomes
`DevOps.md
Sortir des silos.md
`

# Terminal one-liner (bash option)

`for f in *.md; do 
  new=$(echo "$f" | sed -E 's/ [0-9a-fA-F]{32}\.md$/.md/')
  [ "$f" != "$new" ] && mv -n "$f" "$new"
done
`

#Python option

```python
import re
from pathlib import Path

folder = Path("path/to/your/markdown/folder")

# Matches: "Some title abcdef1234567890abcdef1234567890.md"
pattern = re.compile(r"^(?P<title>.+?) [0-9a-fA-F]{32}\.md$")

for md_file in folder.glob("*.md"):
    match = pattern.match(md_file.name)
    
    if match:
        new_name = match.group("title") + ".md"
        new_path = md_file.with_name(new_name)

        # Avoid overwriting an existing file
        if new_path.exists():
            print(f"⚠️ Skipped (already exists): {new_name}")
            continue

        md_file.rename(new_path)
        print(f"Renamed: {md_file.name} → {new_name}")
```