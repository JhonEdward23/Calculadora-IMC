# Calculadora-IMC
Projeto de Aprendizado (Calculadora de IMC), ainda estou meaperfeiçoando devagarinho.

<!DOCTYPE html>
<html lang="pt-br">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Modelo para exercício</title>
    <link rel="stylesheet" href="./Assets/Css/style.css">
</head>
<body>
   <section class="container">
    <h1>CALCULADORA DE IMC</h1>
  
<form action="/" id="form" method="POST">
    <label for="peso">Peso</label>
    <input type="text" id="peso" name="peso">
    <label for="altura">Altura</label>
    <input type="text" id="altura" name="altura">
     <button type="submit">Enviar</button>
</form>

<div id="resultado"></div>
   </section>
   

 </form>


     <script src="./Assets/Js/main.js"></script>
</body>

(JS)// Capturar evento de submit do formulário
const form= document.querySelector('#form');

form.addEventListener('submit', function(e) {
    e.preventDefault();
    const inputPeso = e.target.querySelector('#peso');
    const inputAltura = e.target.querySelector('#altura');

    const peso = Number(inputPeso.value);
    const altura = Number(inputAltura.value);

    if (!peso) {
        setResultado('Peso Inválido', false);
        return;
    }

        if (!altura) {
        setResultado('Altura Inválida', false);
        return;
    }
        const imc = getImc(peso, altura);
        const nivelImc = getNivelImc(imc);
        const msg = `Seu IMC é ${imc}  (${nivelImc}).`;

        setResultado(msg, true);

});

function getNivelImc (imc) {
    const nivel = ['Abaixo do Peso', 'Peso Normal', 'Sobrepeso', 'Obesidade Grau 1',
        'Obesidade Grau 2','Obesidade Grau 3'];

if (imc >= 39.9) return nivel [5];
if (imc >= 34.9) return nivel [4]; 
if (imc >= 29.9) return nivel [3];
if (imc >= 24.9) return nivel [2];
if (imc >= 18.5) return nivel [1];
if (imc < 18.5)  return nivel [0];
}
        

function getImc(peso, altura) {
    const imc= peso/altura **2;
    return imc.toFixed(2);
}

function criaP() {
    const p = document.createElement('p');
    return p;

}

function setResultado(msg, isValid){
    const resultado = document.querySelector('#resultado');
    resultado.innerHTML ='';

    const p = criaP();

        if (isValid) {
            p.classList.add('paragrafo-resultado');
        }else {
        p.classList.add('bad');
        } 
    p.innerHTML = msg;
    resultado.appendChild(p);



} 

@import url('https://fonts.googleapis.com/css2?family=Libre+Franklin:ital,wght@0,100..900;1,100..900&family=Open+Sans:ital,wght@0,300..800;1,300..800&family=Phudu:wght@300..900&display=swap');

:root{
    --primary-color:rgb(77, 55, 26);
}

* {
    box-sizing: border-box;
    outline: 0;
}

body{
    margin: 0;
    padding: 0;
    background: var(--primary-color);
    font-family: 'Open sans', sans-serif;
    font-size: 1.3em;
    line-height: 1.5em;
    background-color: antiquewhite;

}

.container {
    max-width: 640px;
    margin: 50px auto;
    background: #fff;
    padding: 50px ;
    border-radius: 12px;               

}

form input, form label, form button{
    display: block;
    width: 100%;
    margin-bottom: 10px;
}

form input{
    font-size: 24px;
    height: 50px;
    padding: 0 20px;
}

form input:focus{
    outline: 1px solid var(--primary-color);
}

form button{
    border: none;
    background: var(--primary-color);
    color: rgb(209, 201, 178);
    font-size: 16px;
    font-weight: 700;
    height: 50px;
    cursor: pointer;
    margin-top: 20px;
}
 
form button:hover{
    background: var(--primary-color);
}

.paragrafo-resultado, .bad {
    background: #5ff391;
    padding: 10px 20px;
}

.bad {
    background: rgb(169, 48, 70);
}

</html>
