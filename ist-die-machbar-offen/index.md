# Ist die machBar offen?

<img id="icon" style = "max-width: 50%;" onclick="update()"  src="error.svg" alt="Error Symbol"/>
<div id="message" style= "font-size:xx-large; color:#aa593d;">Bitte aktiviere JavaScript!</div>
<br/>
<div style= "color:#aa593d;">Stand: <span id="updateTime"></span> <a onclick="update()">(aktualisieren)</a></div>
<style>
#footer {
    position: fixed;
    bottom: 2em;
    width: 100%;
}
</style>


<script src="jquery-3.5.1.min.js"></script>

<script>
var spaceApiURL = "https://spaceapi.ccc-p.org";

var states = {
    true: {icon:"open.svg", message: "Die machBar ist offen!", color: "#FFCE54", alt:"'Open' door sign"},
    false: {icon:"closed.svg", message: "Die machBar ist geschlossen!", color: "#aa593d", alt:"'Closed' door sign"},
    "error": {icon: "error.svg", message: "Ups! Da ist wohl etwas schiefgelaufen!", color: "#aa593d", alt: "Error Symbol"}
}

var refreshTime = 60; // refresh every x seconds

function setState(state){
    var stateConfig = states[state];

    $("#icon").attr("src", stateConfig.icon);
    $("#icon").attr("alt", stateConfig.alt);
    $("#message").text(stateConfig.message);
    $("#message").css("color", stateConfig.color);
    $("#updateTime").text(new Date().toLocaleString());
}

function onFail(){
    setState("error")
}

function update (){
    $.getJSON(spaceApiURL, function(data){
        try{
            var state = data.state.open;
            if (!(typeof state === "boolean"))
                throw "data.state.open must be boolean!"
            setState(state);
        }
        catch (ex){
            onFail()
        }

    }).fail(onFail)
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