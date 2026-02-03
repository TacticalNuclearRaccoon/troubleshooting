What I want: I want to use the infrmation contained in markdown files as knowledge base for a local model to do RAG. But the md files have useless images inside that will contaminate the info. I want to find each md file in my folder and delete: ![anything here](anything here)

bash option: 
` find . -name "*.md" -type f -exec sed -i -E 's/!\[[^]]*\]\([^)]*\)//g' {} +  `

python: 

```python
import re
from pathlib import Path

folder = Path("path/to/your/markdown/folder")

pattern = re.compile(r'!\[[^\]]*\]\([^)]*\)')

for md_file in folder.rglob("*.md"):
    text = md_file.read_text(encoding="utf-8")
    new_text = pattern.sub("", text)

    if text != new_text:
        md_file.write_text(new_text, encoding="utf-8")
        print(f"Cleaned: {md_file}") ```