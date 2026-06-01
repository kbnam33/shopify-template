> Open `templates/index.json` and find every setting value for keys named `"text"`, `"subheading"`, `"description"`, or any similar content field that contains a plain string without HTML tags. Wrap each plain string value in `<p>` tags.
>
> For example, change:
> ```json
> "text": "Some content here"
> ```
> to:
> ```json
> "text": "<p>Some content here</p>"
> ```
>
> Do this for every plain text string value across all sections in the file. Do not wrap values that are already inside HTML tags or that are not content fields (like color scheme IDs, numbers, or booleans).