---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---
Test markdown

---
<ul>
    {% for post in site.posts %}
        <li>
            <a href="{{site.baseurl}}/{{ post.url }}">{{ post.title }}</a>
            <ul>
                <li>
                    {{ post.excerpt }}
                </li>
            </ul>
        </li>
    {% endfor %}
</ul>
---