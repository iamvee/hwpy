
|   description   |   `HTML`    |     `Markdown`     |   
| ------          | :------     |   :----            | 
|   bold          | `*text*`    |   `<b>text</b>`    | 
|   italic        | `_text_`    |   `<i>text</i>`    | 
|   header 1      | `# text`    |   `<h1>text</h1>`  | 



```python

@markdown
def fun_html(*args, **kwargs):
    return "<h1>hello</h1>


@html
def fun_md(*args, **kwargs):
    return "_italic_ text, and *bold*"


print(fun_html())
# putput: "# hello"

print(fun_md())
# putput: "<i>italic</i> text, and <b>bold</b>

```