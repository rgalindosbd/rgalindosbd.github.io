## Capacitación 

You can use the [editor on GitHub](https://github.com/rgalindosbd/rgalindosbd.github.io/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.


```markdown
Syntax highlighted code block

for i in $(ls /home/labseq/SolariaBiodata/testing/reads202012/); do ln -s /home/labseq/SolariaBiodata/testing/reads202012/$i $i; done
for i in $(ls | cut -d "_" -f-2 | uniq); do mkdir $i; mv ${i}*gz $i; done



./filtradorLecturas_mismaMuestra.sh /home/umaelab/SolariaBiodata/testing/input/ /home/umaelab/SolariaBiodata/testing/t_out/ 12 30 50

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
