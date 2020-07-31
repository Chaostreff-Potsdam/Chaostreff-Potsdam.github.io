# Ist die Machbar offen?

<img id="icon" style = "max-width: 50%;" onclick="update()"/>
<div id="message" style= "font-size:xx-large; color:#aa593d;">Die Machbar ist geschlossen!</div>
<br/>
<div style= "color:#aa593d;">Stand: <span id="updateTime"></span> <a onclick="update()">(aktualisieren)</a></div>
<style>
#footer {
    position: fixed;
    bottom: 2em;
    width: 100%;
}
</style>


<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>

<script>
var spaceApiURL = "https://spaceapi.ccc-p.org/";

var states = {
    true: {icon:"open.svg", message: "Die Machbar ist offen!", color: "#FFCE54"},
    false: {icon:"closed.svg", message: "Die Machbar ist geschlossen!", color: "#aa593d"}
}

var refreshTime = 60; // refresh every x seconds

function setState(state){
    var stateConfig = states[state];

    $("#icon").attr("src", stateConfig.icon);
    $("#message").text(stateConfig.message);
    $("#message").css("color", stateConfig.color);
    $("#updateTime").text(new Date().toLocaleString());
}

function update (){
    $.getJSON(spaceApiURL, function(data){
        var state = data.state.open;
        setState(state);
    })
}

function main(){
    update();
    setInterval(update, refreshTime * 1000); // update state once every refreshTime seconds
}

$(document).ready(main);
</script>

<div id="footer">
Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon"> www.flaticon.com</a>
</div>