---
layout: page
title: Test Page
permalink: /test/
---

two files in the `/docs/` directory root:
* `test.md`  with `permalink: /test`
* `test_sub.md` with `permalink: /test/sub`

-------------------

expected result `https://mysite.com/my_baseurl/test/sub`

-------------------

n | ln format                                    | rendered ln                         | markdown                                              | rendered href | note                          
--|----------------------------------------------|-------------------------------------|-------------------------------------------------------|--------------------------------|---
1 | raw permalink                                | [ln](/test/sub)                     | {% raw %}`[ln](/test/sub)`{% endraw %}                | `"/test/sub`  | missing baseurl
2 | permalink w permalink `/test` auto-appended? | [ln](sub)                           | {% raw %}`[ln](sub)`{% endraw %}                      | `"sub`        | works but is horrible
3 | link tag                                     | [ln]({% link test_sub.md %})        | {% raw %}`[ln]({% link test_sub.md %})`{% endraw %}   | `"/test/sub`  | missing baseurl
4 | relative_url                                 | [ln]({{ sub | relative_url }})      | {% raw %}`[ln]({{ sub | relative_url }})`{% endraw %} | `""`          | links to current page (/test/)
5 | absolute_url                                 | [ln]({{ sub | absolute_url }})      | {% raw %}`[ln]({{ sub | absolute_url }})`{% endraw %} | `""`          | links to current page (/test/)

----------------------------------------
