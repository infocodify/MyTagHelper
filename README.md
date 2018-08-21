# MyTagHelper
Create your Taghelper in asp.Net Core 2

### Follow the steps:

1.  Create an asp.Net Core 2 Web Application Project

2.  Right Click on the the Project and Create a Class

<code>
using Microsoft.AspNetCore.Razor.TagHelpers;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace TagHelpers
{
    public class MyTagHelpers : TagHelper
    {
        public int Count { get; set; }

        public override async Task ProcessAsync(TagHelperContext context, TagHelperOutput output)
        {
            for (int i = 0; i < Count; i++)
            {
                output.Content.AppendHtml(await output.GetChildContentAsync(useCachedResult:false));
            }
        }

    }
}
</code>
