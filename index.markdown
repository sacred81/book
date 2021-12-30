---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

---
<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
<div id="chart_div"></div>
<script defer type="text/javascript">
    google.charts.load('current', {'packages':['corechart']});
    google.charts.setOnLoadCallback(drawChart);
    function drawChart() {
        var data = new google.visualization.DataTable();
        data.addColumn('string', 'category');
        data.addColumn('number', 'amount');

        {%- for e in site.posts.first.ex -%}
            {% if e.amo %}
        data.addRow(['{{e.dis}}', {{e.amo}}]);
            {%- endif -%}
        {%- endfor %}

        if (data.getNumberOfRows() > 0) {
            data.sort({column: 1, desc: true});

            {% assign chart-title = site.posts.first.title | split: ' ' %}
            {%- assign chart-title = chart-title[0] -%}
            var options = {'title':'{{ chart-title }}'};
            var chart = new google.visualization.PieChart(document.getElementById('chart_div'));
            chart.draw(data, options);
        }
    }
</script>
<ul>
    {% for post in site.posts %}
        <li>
            <a href="{{site.baseurl}}{{ post.url }}">{{ post.title }}</a>
            <ul>
                <li>
                    {{ post.excerpt }}
                </li>
            </ul>
        </li>
    {% endfor %}
</ul>
---