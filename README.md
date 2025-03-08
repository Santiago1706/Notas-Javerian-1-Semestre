# Notas-Javerian-1-Semestre
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plataforma de Notas</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
        }
        
        #menu {
            width: 250px;
            background: #333;
            color: white;
            padding: 20px;
            height: 100vh;
            overflow-y: auto;
            position: fixed;
        }
        
        #menu h2 {
            text-align: center;
        }
        
        #menu a {
            color: white;
            display: block;
            padding: 15px;
            text-decoration: none;
            border-bottom: 1px solid #555;
        }
        
        #menu a:hover {
            background: #555;
        }
        
        #contenido {
            flex-grow: 1;
            padding: 30px;
            background: #f4f4f4;
            margin-left: 270px;
        }
        
        .materia {
            background: white;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        
        th, td {
            border: 1px solid black;
            padding: 10px;
            text-align: left;
        }
        
        th {
            background: #ddd;
        }
        
        .aprobado {
            background-color: #b2ffb2;
        }
        
        .reprobado {
            background-color: #ffb2b2;
        }
        
        .nota-definitiva {
            font-size: 1.2em;
            font-weight: bold;
            margin-top: 10px;
            padding: 10px;
            display: inline-block;
            border-radius: 5px;
        }
        
        .nota.aprobado {
            background-color: #b2ffb2;
        }
        
        .nota.reprobado {
            background-color: #ffb2b2;
        }
    </style>
    <script>
        function calcularNotas() {
            document.querySelectorAll(".materia").forEach(materia => {
                let total = 0;
                let porcentajeTotal = 0;
                let filas = materia.querySelectorAll("table tr");
                
                filas.forEach((fila, index) => {
                    if (index > 0) {
                        let porcentaje = parseFloat(fila.cells[1].innerText) / 100;
                        let nota = parseFloat(fila.cells[2].innerText);
                        total += porcentaje * nota;
                        porcentajeTotal += porcentaje;

                        if (nota >= 2.96) {
                            fila.cells[2].classList.add("aprobado");
                        } else {
                            fila.cells[2].classList.add("reprobado");
                        }
                    }
                });
                
                let definitiva = (total / porcentajeTotal).toFixed(2);
                let resultado = document.createElement("p");
                resultado.classList.add("nota-definitiva");
                resultado.innerText = "Nota Definitiva: " + definitiva;
                
                if (definitiva >= 2.96) {
                    resultado.classList.add("aprobado");
                } else {
                    resultado.classList.add("reprobado");
                }
                
                materia.appendChild(resultado);
            });
        }
        
        window.onload = calcularNotas;
    </script>
</head>
<body>
    <div id="menu">
        <h2>Materias</h2>
        <a href="#matematica">Matemáticas</a>
        <a href="#ciencias">Ciencias</a>
        <a href="#historia">Historia</a>
        <a href="#literatura">Literatura</a>
        <a href="#fisica">Física</a>
        <a href="#quimica">Química</a>
        <a href="#biologia">Biología</a>
        <a href="#filosofia">Filosofía</a>
    </div>
    
    <div id="contenido">
        <section id="matematica" class="materia">
            <h2>Matemáticas</h2>
            <p><strong>Profesor:</strong> Juan Pérez</p>
            <p><strong>Créditos:</strong> 3</p>
            <table>
                <tr>
                    <th>Descripción</th>
                    <th>Porcentaje</th>
                    <th>Nota</th>
                </tr>
                <tr>
                    <td>Examen parcial</td>
                    <td>40%</td>
                    <td class="nota">3.5</td>
                </tr>
                <tr>
                    <td>Tarea</td>
                    <td>20%</td>
                    <td class="nota">2.8</td>
                </tr>
                <tr>
                    <td>Proyecto final</td>
                    <td>40%</td>
                    <td class="nota">4.0</td>
                </tr>
            </table>
        </section>
        
        <section id="ciencias" class="materia">
            <h2>Ciencias</h2>
            <p><strong>Profesor:</strong> María López</p>
            <p><strong>Créditos:</strong> 4</p>
            <table>
                <tr>
                    <th>Descripción</th>
                    <th>Porcentaje</th>
                    <th>Nota</th>
                </tr>
                <tr>
                    <td>Examen parcial</td>
                    <td>40%</td>
                    <td class="nota">2.5</td>
                </tr>
                <tr>
                    <td>Laboratorio</td>
                    <td>30%</td>
                    <td class="nota">3,0</td>
                </tr>
                <tr>
                    <td>Proyecto final</td>
                    <td>30%</td>
                    <td class="nota">5.0</td>
                </tr>
            </table>
        </section>
    </div>
</body>
</html>
