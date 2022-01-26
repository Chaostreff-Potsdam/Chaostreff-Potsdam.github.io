{% assign online = site.data.covid-info.online %}
{% assign url = site.data.covid-info.meeting-url %}

<div style="background: #b00; padding: 1em; border-radius: 15px;">
Die wöchentlichen Vor-Ort-Treffen finden derzeit aufgrund des Coronarisikos {% if online %} nicht {% else %} nur bei gutem Wetter im Freien {% endif %} statt!

{% if online %} Stattdessen {% else %} Bei schlechtem Wetter {% endif %} treffen wir uns mittwochs ab 19 Uhr hier: <a href="{{ url }}">{{ url }}</a>.

{% if online %}
Weitere Online-Kommunikationskanäle bei Chaosentzug:
{% else %}
Ob das wöchentliche Treffen vor Ort oder online stattfindet, wird im Laufe des Mittwochs über unsere Online-Kommunikationskanäle bekannt gegeben:
{% endif %}
<a href="#unsere-kommunikationskanäle">hier!</a>
</div>