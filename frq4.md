<head>
    
 <style type="text/css">
.root {
    display: block;
}

.body {
    text-align:center;
}

.p {
    font-family:monospace;
}

.table {
    margin:auto;
}

td {
    width:50px;
    height:50px;
    border: 1px solid black;
    font-size:40px;
    text-align:center;
    font-family:arial, helvetica, sans-serif;
}

</style>

</head>

<script>
    function drawLightBoard() {
        let url = "https://womeninstem.tk/api/lightboard/3/3";

        fetch(url)
			.then(response => response.json())
			.then(result => {
                for(var i = 0; i < result.length; i++) {
                    var cube = result[i];
                    var cell = document.getElementById("cell" + cube.row + cube.column);
                    cell.style.backgroundColor =  RGB2HTML(cube.light.red, cube.light.green,cube.light.blue);
                    console.log(RGB2HTML(cube.light.red, cube.light.green,cube.light.blue));
                }
			})
			.catch(error => console.log('error', error));
    }

    function RGB2HTML(red, green, blue)
    {
        var decColor =0x1000000+ blue + 0x100 * green + 0x10000 *red ;
        return '#'+decColor.toString(16).substr(1);
    }

</script>
<body>
    <table>
        <tr>
            <td id="cell00" ></td>
            <td id="cell01" ></td>
            <td id="cell02" ></td>
        </tr>
        <tr>
            <td id="cell10" ></td>
            <td id="cell11" ></td>
            <td id="cell12" ></td>
        </tr>
        <tr>
            <td id="cell20" ></td>
            <td id="cell21" ></td>
            <td id="cell22" ></td>
        </tr>
    </table>

    <div>
        <input type="button" value="Show LightBoard" id = "button1" onclick="drawLightBoard();">
    </div>


</body>
