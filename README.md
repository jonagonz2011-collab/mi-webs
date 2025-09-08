# piedra papel o tijera
<!DOCTYPE html>

<head>
    <style>
        h1 {
            color: blue;
            text-align: center;
        }

        .iconos {
            width: 150px;
            height: 150px;
        }
        .icono {
            width: 150px;
            height: 150px;
        }
        
        .alineacionObjetos{
            display: flex;
            justify-content: space-evenly;
        }

        .visible {
            display: inline-block;
        }

        .noVisible {
            display: none;
        }
        .bnt {
            border: none;
            background-color: white;
        }
    </style>
</head>

<body>
    <h1>piedra papel o tijera</h1>
    <div class="alineacionObjetos"> 
        <div style="display: inline-block;">
            <table border="0">
                <tr>
                    <td class="visible" id="j-0">
                        <button value="0" onclick="obtenerJUGADA(this.value)" class="bnt">
                            <img src="https://img.freepik.com/fotos-premium/piedra-natural-aislado-sobre-fondo-blanco_153912-10386.jpg?w=740"
                                class="iconos">
                        </button>
                    </td>
                    <td class="visible" id="j-1">
                        <button value="1" onclick="obtenerJUGADA(this.value)"class="bnt">
                            <img src="https://valman.com.uy/mvdpanel_productos_img/PAPEL_CALCO_95_GRS_210_x_297_mm_500_h.jpg"
                                class="iconos">
                        </button>
                    </td>
                    <td class="visible" id="j-2">
                        <button value="2" onclick="obtenerJUGADA(this.value)"class="bnt">
                            <img src="https://http2.mlstatic.com/D_NQ_NP_827975-MLU70343444246_072023-O.webp" 
                                class="iconos">
                        </button>
                    </td>
                </tr>
            </table>
            
        </div>
    
    
        <div style="display: inline-block;">
            <table>
                <tr>
                    <td class="noVisible" id="m-0">
                        <img src="https://img.freepik.com/fotos-premium/piedra-natural-aislado-sobre-fondo-blanco_153912-10386.jpg?w=740"
                                class="icono">
                    </td>
                    <td class="noVisible" id="m-1">
                         <img src="https://valman.com.uy/mvdpanel_productos_img/PAPEL_CALCO_95_GRS_210_x_297_mm_500_h.jpg"
                                class="icono">
                    </td>
                    <td class="noVisible" id="m-2">
                         <img src="https://http2.mlstatic.com/D_NQ_NP_827975-MLU70343444246_072023-O.webp" class="icono">
                    </td>
                </tr>
            </table>
        </div>
        
    </div>
    
    
    <p id="jugadamaquina"></p>
    <p id="resultado"></p>
    <p>Jugador: <span id="puntosJugador"></span></p>
    <p>Maquina: <span id="puntosMaquina"></span></P>
    <script>
        let puntosJugador = 0
        let puntosMaquina = 0

        const ppt = ["piedra", "papel", "tijera"]

        //Defino elementos HTML por ID
        let mostrarRES = document.getElementById("resultado")
        let mostrarJUGADAMAQUINA = document.getElementById("jugadamaquina")
        let mostrarPUNTOSMAQUINA = document.getElementById("puntosMaquina")
        let mostrarPUNTOSJUGADOR = document.getElementById("puntosJugador")

        var resultado = ""
        function obtenerJUGADA(miJugada) {
            let posJUGADA = Math.floor(Math.random() * 3);

            if (posJUGADA == miJugada) { resultado = "empate" }
            if (posJUGADA == 0 && miJugada == 1) {resultado = "ganaste";puntosJugador++}
            if (posJUGADA == 1 && miJugada == 0) {resultado = "perdiste";puntosMaquina++}
            if (posJUGADA == 0 && miJugada == 2) { resultado = "perdiste", puntosMaquina++ }
            if (posJUGADA == 2 && miJugada == 0) { resultado = "ganaste", puntosJugador++ }
            if (posJUGADA == 1 && miJugada == 2) { resultado = "ganaste", puntosJugador++ }
            if (posJUGADA == 2 && miJugada == 1) { resultado = "perdiste", puntosMaquina++ }

            
            mostrarRES.innerHTML = resultado;       
            mostrarPUNTOSMAQUINA.innerHTML = puntosMaquina
            mostrarPUNTOSJUGADOR.innerHTML = puntosJugador

            document.getElementById("j-0").className = "noVisible";
            document.getElementById("j-1").className = "noVisible";
            document.getElementById("j-2").className = "noVisible";
            document.getElementById("j-"+miJugada).className = "visible";

            document.getElementById("m-0").className = "noVisible";
            document.getElementById("m-1").className = "noVisible";
            document.getElementById("m-2").className = "noVisible";
            document.getElementById("m-"+posJUGADA).className = "visible";

            setTimeout(function () {
                document.getElementById("j-0").className = "visible";
                document.getElementById("j-1").className = "visible";
                document.getElementById("j-2").className = "visible";  
                
                document.getElementById("m-0").className = "visible";
                document.getElementById("m-1").className = "visible";
                document.getElementById("m-2").className = "visible";  
                

            }, 3000);



 
        }

    </script>

</body>

</html>
