---
front matter things here
---
{%- capture code -%}
/* Some js code */
const redis = require('redis');
const host = <HOSTNAME>;
{%- endcapture -%}

{% include code_snippet.md code=code language='javascript' %}

{%- capture code -%}
# Some ruby code
t = Time.now
t.succ  
{%- endcapture -%}

{% include code_snippet.md code=code language='ruby' %}