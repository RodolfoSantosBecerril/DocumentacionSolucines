function sumar(){
    const forma = document.getElementById('forma');
    let operandoA = forma['operandoA'];
    let operandoB = forma['operandoB'];
    let operandoC = forma['operandoC'];
    let resultado =  
    parseFloat(operandoC.value)/(((1-0.2*(parseFloat(operandoA.value)/ parseFloat(operandoB.value))))-((0.8)*(Math.pow(parseFloat(operandoA.value)/(parseFloat(operandoB.value)), 2)))); 
    if(isNaN(resultado))
        resultado = 'La operación no incluye números';
    document.getElementById('resultado').innerHTML = `El gasto máximo es: ${resultado}`;
    console.log(`Resultado: ${resultado}`);
    return resultado;
}

function sumar1(){
    const forma = document.getElementById('forma1');
    let operandoA = forma['operandoA'];
    let operandoB = forma['operandoB'];
    let operandoC = forma['operandoC'];
    let resultado =  
    parseFloat(operandoA.value)/(parseFloat(operandoB.value)*parseFloat(operandoC.value))  ; 
    if(isNaN(resultado))
        resultado = 'La operación no incluye números';
    document.getElementById('resultado1').innerHTML = `El resultado es: ${resultado}`;
    console.log(`Resultado: ${resultado}`);
    return resultado;
}
function sumar2(){
    const forma = document.getElementById('forma2');
    let operandoA = forma['operandoA'];
    let operandoB = forma['operandoB'];
    let operandoC = forma['operandoC'];
    let resultado =  
    parseFloat(operandoA.value)/(parseFloat(operandoB.value)*parseFloat(operandoC.value))  ;   
    if(isNaN(resultado))
        resultado = 'La operación no incluye números';
    document.getElementById('resultado2').innerHTML = `El resultado es: ${resultado}`;
    console.log(`Resultado: ${resultado}`);
    return resultado;
}
function sumar3(){
    const forma = document.getElementById('forma3');
    let operandoA = forma['operandoA'];
    let operandoB = forma['operandoB'];
    let operandoC = forma['operandoC'];
    let operandoD = forma['operandoD'];
    let operandoE = forma['operandoE'];

    let resultado =  
    parseFloat(operandoA.value) *((parseFloat(operandoB.value)*(parseFloat(operandoC.value)))/(parseFloat(operandoD.value)*(parseFloat(operandoE.value))) ) ;   
    if(isNaN(resultado))
        resultado = 'La operación no incluye números';
    document.getElementById('resultado3').innerHTML = `El resultado es: ${resultado}`;
    console.log(`Resultado: ${resultado}`);
    return resultado;
}

    
function sumar4(){
    //   const forma4 = document.getElementById('forma4');
       
    //////
      let operandoC = parseFloat(prompt(`Ingresa el gasto máximo actual: `)); 
      let paresalerta =parseFloat(prompt(`Ingresa el intervalo de la presión actual: `));
      let operandoA = parseFloat(prompt(`Ingresa presión estatica.: `));

      let operandoD = parseFloat(prompt(`Ingresa el gasto máximo futuro: `));
      let paresalerta1 =parseFloat(prompt(`Ingresa el intervalo de la presión para el caso futuro: `));

      let operandoE = parseFloat(prompt(`Ingresa la presión maxima para el caso futuro: `));

 
      let pares1 = [];
      
      let pares = [];
      let res =[];
      if (isNaN(paresalerta)) {
      
        alert('Debes introducir un valor');
      }
      if(isNaN(operandoA)){
          alert('Debes introducir un numero valido');
      }
       
      if(paresalerta<=operandoA){
          for (var i = 0; i<= operandoA; i+=paresalerta)
          {   
             resultado=parseFloat(operandoC)*(((1-0.2*(parseFloat(i)/ parseFloat(operandoA))))-((0.8)*(Math.pow(parseFloat(i)/(parseFloat(operandoA)), 2)))); 
            
              pares.push(i) ;
            res.push(resultado);
         
          }
      }
   
      let res1 =[];
      if (isNaN(paresalerta1)) {
      
        alert('Debes introducir un valor');
      }
      if(isNaN(operandoA)){
          alert('Debes introducir un numero valido');
      }
       
      if(paresalerta1<=operandoE){
          for (var i = 0; i<= operandoA  ; i+=paresalerta1)
          {   
             
             resultado1=parseFloat(operandoD)*(((1-0.2*(parseFloat(i)/ parseFloat(operandoE))))-((0.8)*(Math.pow(parseFloat(i)/(parseFloat(operandoE)), 2)))); 
      
              pares1.push(i) ;
            
            res1.push(resultado1);
          }
      }
     
    
   
      document.getElementById('salida1').innerHTML = pares;
      document.getElementById('salida2').innerHTML = res;
      document.getElementById('salida3').innerHTML = pares1;
      document.getElementById('salida4').innerHTML = res1;

      console.log('funciona');
   
      const $grafica = document.querySelector("#grafica");
   // Las etiquetas son las que van en el eje X. 
   let etiquetas = document.getElementById('salida1').innerHTML = pares; 
   let etiquetas1 = document.getElementById('salida3').innerHTML = pares1; 

    // GASTO SALIDA 2
   // Podemos tener varios conjuntos de datos
   let datosVentas2020 = {
       label: "Curvas IPR",
       data:document.getElementById('salida2').innerHTML = res , // PROFUNDIDAD SALIDA 1 La data es un arreglo que debe tener la misma cantidad de valores que la cantidad de etiquetas
       backgroundColor: 'rgba(54, 162, 235, 0.2)', // Color de fondo
       borderColor: 'rgba(54, 162, 235, 1)', // Color del borde
       borderWidth: 1,// Ancho del borde
   };
    
   const datosVentas2021 = {
       label: "IPR Futuro",
       data: document.getElementById('salida4').innerHTML = res1 , // La data es un arreglo que debe tener la misma cantidad de valores que la cantidad de etiquetas
       backgroundColor: 'rgba(255, 159, 64, 0.2)',// Color de fondo
       borderColor: 'rgba(255, 159, 64, 1)',// Color del borde
       borderWidth: 1,// Ancho del borde
   };
    
   new Chart($grafica, {
       type: 'line',// Tipo de gráfica
       data: {
           labels: etiquetas, etiquetas1,
           datasets: [
               datosVentas2020,
               datosVentas2021,
               // Aquí más datos...
           ]
       },
       options: {
           scales: {
               yAxes: [{
                   ticks: {
                       beginAtZero: true
                   }
               }],
           },
       }
   });
   }
   
 

//---------------------------------------------------------------------------------------------------GRAFICADORA
// Obtener una referencia al elemento canvas del DOM
const $grafica = document.querySelector("#grafica");
// Las etiquetas son las que van en el eje X. 
let etiquetas = ["0", "500", "1000", "1500", "2000", "2500", "3000", "3500"] // GASTO SALIDA 2
// Podemos tener varios conjuntos de datos
let datosVentas2020 = {
    label: "Curvas IPR",
    data:[ ], // "3500", "3000", "2500", "2000", "1500","1000", "500","0"  PROFUNDIDAD SALIDA 1 La data es un arreglo que debe tener la misma cantidad de valores que la cantidad de etiquetas
    backgroundColor: 'rgba(54, 162, 235, 0.2)', // Color de fondo
    borderColor: 'rgba(54, 162, 235, 1)', // Color del borde
    borderWidth: 1,// Ancho del borde
};
 
const datosVentas2021 = {
    label: "IPR Futura",
    data: [ ], // La data es un arreglo que debe tener la misma cantidad de valores que la cantidad de etiquetas
    backgroundColor: 'rgba(255, 159, 64, 0.2)',// Color de fondo
    borderColor: 'rgba(255, 159, 64, 1)',// Color del borde
    borderWidth: 1,// Ancho del borde
};
 
new Chart($grafica, {
    type: 'line',// Tipo de gráfica
    data: {
        labels: etiquetas,
        datasets: [
            datosVentas2020,
            datosVentas2021,
            // Aquí más datos...
        ]
    },
    options: {
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero: true
                }
            }],
        },
    }
});