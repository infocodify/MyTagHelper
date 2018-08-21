# MyTagHelper
Create your Taghelper in asp.Net Core 2

### Follow the steps:

1.  Create an asp.Net Core 2 Web Application Project

2.  Right Click on the the Project and Create a Class

```csharp
using Microsoft.AspNetCore.Razor.TagHelpers;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace TagHelpers
{
    //MyTag will be the your own Tag Helper
    public class MyTagHelpers : TagHelper
    {
        public int Count { get; set; }
        
        //Right Click on the TagHelper and Peek Definition, copy the abstract class and override 
        public override async Task ProcessAsync(TagHelperContext context, TagHelperOutput output)
        {
            for (int i = 0; i < Count; i++)
            {
                output.Content.AppendHtml(await output.GetChildContentAsync(useCachedResult:false));
            }
        }

    }
}
```
3.  In the ViewImports.cshtml add your own Taghelper assembly (your web app name)
```csharp
@using TagHelpers
@namespace TagHelpers.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

@addTagHelper *, TagHelpers
```

4. Open Index.cshtml, add the following code run the application and test your TagHelper
```html
@page
@model IndexModel

@{
    ViewData["Title"] = "My Own Taghelpers";
}

<h1>How to use your own Tag-Helpers</h1>

<my-tag-helpers count="6">
    <p>Text Repeated 6 - Times</p>
</my-tag-helpers>
```
