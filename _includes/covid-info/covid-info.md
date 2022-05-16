{% assign mode = site.data.covid-info.mode %}
{% assign url = site.data.covid-info.meeting-url %}

{% if mode %}
<div style="background: #b00; padding: 1em; border-radius: 15px;">
  {% include covid-info/{{ mode }}.md %}
</div>
{% endif %}