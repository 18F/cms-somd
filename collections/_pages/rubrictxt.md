---
layout: wide
title: Rubric
---

<div style="width: 90%; margin: auto; margin-top: 2em; margin-bottom: 2em;">
    <em>You can also view this rubric in <a href="{{ '/rubric' | prepend: site.baseurl }}">tabular form</a>.</em>
</div>
<div style="width: 90%; margin: auto; margin-top: 2em; margin-bottom: 2em;">
{% for section in site.data.rubric %}
    {% assign mod = forloop.index | modulo: 2 %}
        <h1>{{section.header}}</h1>
        <b>{{section.question}}</b>
        <hr noshade aria-hidden="true">
        <div class="usa-summary-box">
            <div class="usa-summary-box__body">
                <h2 class="usa-summary-box__heading">
                    Why this matters...
                </h2>
                <div class="usa-summary-box__text">
                    {{section.wtm}}
                </div>
            </div>
        </div>
{% for priority in section.priorities %}
{% for dimension in priority.dimensions %}
    <div class="grid-row"> 
    {% if forloop.first == true %}<h3>{{ priority.label }}</h3>{% endif %}
    </div>
    <div class="grid-row">
        <div class="grid-col-8 grid-offset-1">
        {% for tip in dimension.tips %}
            <h4>{{ tip }}</h4> 
        {% endfor %}
            <ul>
                <li><b class="danger-text">Bad</b>: {{dimension.red}} </li>
                <li><b class="warning-text">Meh</b>: {{dimension.yellow}} </li>
                <li><b class="ok-text">Good</b>: {{dimension.green}} </li>
            </ul>
            Related course lessons: {%- include rubrictopagelink.html id=dimension.id sep=", "-%}
            {% unless forloop.last %}<hr noshade width="20%" aria-hidden="true">{% endunless %}
        </div>
    </div>
{% endfor %}
{% endfor %}
{% endfor %}
</div>