# realtime-issue-tracker
A real-time issue was faced while  developing the app and with the solution.  

# template 

```md
## Link

[Markdown Live Preview](https://markdownlivepreview.com/).

## Blockquotes

> Markdown is a lightweight

## Blocks of code

```
let message = 'Hello world';
alert(message);
```

## Lists

- [ ] What is Angular and why is it used?
```

## ``[WEB-001]`` : `$event.target.value` not resolved in Angular template 

`Object possible null`
```html
<label for="select"></label><select name="" id="select" (change)="onChange($event.target.value)">
    <option value="">Select combo</option>
    <option value="Value1">Text1</option>
    <option value="Value2">Text2</option>
    <option value="Value3">Text3</option>
</select>
```

#### Solution

```html
<select (change)="onChange($any($event.target).value)">
```


