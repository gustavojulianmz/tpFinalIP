# tpFinalIP
Trabajo Practico Final IP
<?php


// a) Carga automatica de la matriz de temperaturas

$matrizTemp = array();

function tempAutomatica ()  {
    $matrizTemp = [
        [30, 28, 26, 22, 18, 12, 10, 14, 17, 20, 25, 29],
        [33, 30, 27, 22, 19, 13, 11, 15, 18, 21, 26, 31],
        [34, 32, 29, 21, 18, 14, 12, 16, 18, 21, 27, 32],
        [33, 31, 28, 22, 18, 13, 11, 14, 17, 22, 26, 31],
        [32, 30, 28, 22, 17, 12, 9, 13, 16, 20, 24, 30],
        [32, 30, 27, 23, 19, 14, 12, 11, 17, 23, 25, 29],
        [31, 29, 28, 21, 19, 13, 10, 12, 16, 22, 27, 29],
        [30, 28, 26, 20, 16, 12, 11, 13, 17, 21, 28, 30],
        [31, 29, 27, 21, 17, 12, 11, 15, 18, 22, 26, 30],
        [32, 30, 27, 20, 16, 13, 13, 15, 19, 23, 28, 31],
    ];
    return $matrizTemp;
}

// b) Carga manual de la matriz de temperaturas
/**
 * Summary of cargaManual
 * @param array $matrizTemp
 * @return void
 */
function cargaManual ( array $matrizTemp){
    for ($filaAnio = 0; $filaAnio < count($matrizTemp); $filaAnio++){
        for ($columMes = 0; $columMes < count($matrizTemp); $columMes++){
            echo "Ingrese la temperatura:";
            $matrizTemp[$filaAnio][$columMes] = trim(fgets(STDIN));
        }


    }

}

// c) Mostrar el contenido de la matriz por filas y columnas.
/**
 * Summary of mostrarFila
 * @param array $matrizTemp
 * @return void
 */
function mostrarFila ( array $matrizTemp){
    for ($filaAnio = 0; $filaAnio < count($matrizTemp); $filaAnio++){
        echo $matrizTemp[$filaAnio] ."\n";
    }
}

/**
 * Summary of mostrarColumna
 * @param array $matrizTemp
 * @return void
 */
function mostrarColumna ( array $matrizTemp){
    for ($columMes = 0; $columMes < count($matrizTemp); $columMes++){
        echo $matrizTemp[$columMes] . "\n";

    }
    
}

// d) Mostrar, dado un año y un mes, el valor de temperatura correspondiente
/**
 * Summary of mes
 * @param int $nro
 * @return string
 */
function mes(int $nro): string {
    $nombre = "";
    
    switch ($nro) {
        case 0: $nombre = "enero"; break;
        case 1: $nombre = "febrero"; break;
        case 2: $nombre = "marzo"; break;
        case 3: $nombre = "abril"; break;
        case 4: $nombre = "mayo"; break;
        case 5: $nombre = "junio"; break;
        case 6: $nombre = "julio"; break;
        case 7: $nombre = "agosto"; break;
        case 8: $nombre = "septiembre"; break;
        case 9: $nombre = "octubre"; break;
        case 10: $nombre = "noviembre"; break;
        case 11: $nombre = "diciembre"; break;
    }
    
    return $nombre;
}
/**
 * Summary of mostrarAnioMes
 * @param array $matrizTemp
 * @param int $filaAnio
 * @param mixed $columMes
 * @return void
 */
function mostrarAnioMes ( array $matrizTemp, int $filaAnio, $columMes){
    for ($columMes = 0; $columMes < count($matrizTemp[0]); $columMes++) {
        echo mes($columMes) . " [" . $filaAnio . "]: " . $matrizTemp[$filaAnio][$columMes] . "\n";
    }

}

// e) Mostrar para un determinado año, las temperaturas de todos los meses.
 /**
  * Summary of mostrarTempMeses
  * @param array $matrizTemp
  * @param int $anio
  * @return void
  */
 function mostrarTempMeses ( array $matrizTemp, int $anio){
    $filaAnio = $anio - 2014;
    for ($columMes = 0; $columMes < count($matrizTemp[0]); $columMes++) {
        echo $matrizTemp[$filaAnio][$columMes] . "\n";
    }
 }

 // f) Mostrar para un mes determinado, las temperaturas de todos los años y el promedio.


 /**
  * Summary of mostrarPromTemp
  * @param array $matrizTemp
  * @param int $mes
  * @return float
  */
 function mostrarPromTemp(array $matrizTemp, int $mes): float {

    $suma = 0;
    $promedio = 0;

    for ($filaAnio = 0; $filaAnio < count($matrizTemp); $filaAnio++){
        $suma = $suma + $matrizTemp[$filaAnio][$mes];
    }
    $promedio = $suma / count($matrizTemp);
    return $promedio;
}
 // g) Hallar las temperaturas máximas y mínimas, indicando año y mes a los que
//     corresponden. Si el máximo o mínimo se repite, mostrar el primero encontrado.

// Dividido en dos modulos, uno para la temperatura maxima y otro para la minima.
/**
 * Summary of tempMax
 * @param array $matrizTemp
 * @param int $maxTemp
 * @param mixed $maxAnio
 * @param mixed $maxMes
 * @return array
 */
function tempMax ( array $matrizTemp, int $maxTemp, $maxAnio, $maxMes){

    $maxTemp = 0;
    $maxAnio = 0;
    $maxMes = 0;

    for ($filaAnio = 0; $filaAnio <= 9; $filaAnio++) {
        for ($columMes = 0; $columMes <= 11; $columMes++) {
            if ($matrizTemp[$filaAnio][$columMes] > $maxTemp) {
                $maxTemp = $matrizTemp[$filaAnio][$columMes];
                $maxAnio = 2014 + $filaAnio;
                $maxMes = $columMes + 0;
            }
        }

}
// RETORNA una arreglo asociativo con los maximos
return [
    "maxTemp" => $maxTemp,
    "maxAnio" => $maxAnio,
    "maxMes" => $maxMes
];
}

/**
 * Summary of tempMin
 * @param array $matrizTemp
 * @param int $minTemp
 * @param mixed $minAnio
 * @param mixed $minMes
 * @return array
 */
function tempMin ( array $matrizTemp, int $minTemp, $minAnio, $minMes){

    $minTemp = 9999;
    $minAnio = 0;
    $minMes = 0;

    for ($filaAnio = 0; $filaAnio < count($matrizTemp); $filaAnio++) {
        for ($columMes = 0; $columMes < count($matrizTemp[0]); $columMes++) {
            if ($matrizTemp[$filaAnio][$columMes] < $minTemp) {
                $minTemp = $matrizTemp[$filaAnio][$columMes];
                $minAnio = 2014 + $filaAnio;
                $minMes = $columMes + 0;
            }
        }
    }
// Retorna un arreglo asociativo con los minimos
    return [
        "minTemp" => $minTemp,
        "minAnio" => $minAnio,
        "minMes" => $minMes
    ];
}

/**
 * Summary of primavera
 * @param array $matrizTemp
 * @return array
 */
function primavera ( array $matrizTemp, ) {

    $matrizPrim = array ();

    for ($anio = 0; $anio < count($matrizTemp); $anio++) {
        for ($mes = 9; $mes <= 11; $mes++) {
            echo $matrizTemp[$anio][$mes] . "\n"; // Muestra los valores de los últimos tres meses para cada fila

}
$matrizPrim[$anio] = $matrizTemp[$anio]; //copia cada fila completaa
    }
    return $matrizPrim;
}

// i) Crear y mostrar un arreglo bidimensional con los datos de los últimos 5 años de invierno (jul-ago-sep). 
/**
 * Summary of invierno
 * @param array $matrizTemp
 * @return array[]
 */
function invierno ( array $matrizTemp){

    $matrizInvierno = array();

    for ($filaAnio = 5; $filaAnio <= 9; $filaAnio++) {
        $matrizInvierno[$filaAnio][0] = $matrizTemp[$filaAnio][6]; // Julio
        $matrizInvierno[$filaAnio][1] = $matrizTemp[$filaAnio][7]; // Agosto
        $matrizInvierno[$filaAnio][2] = $matrizTemp[$filaAnio][8]; // Septiembre
    }
    return $matrizInvierno;
}


function mostrarInvierno ( array $matrizTemp){

    for ($filaAnio = 0; $filaAnio < count($matrizTemp); $filaAnio++) {
        for ($columMes = 0; $columMes < count($matrizTemp[$filaAnio]); $columMes++) {
            echo $matrizTemp[$filaAnio][$columMes] . "\n";
        }
    }

}

// J) Crear un arreglo asociativo que contenga en la primera posición con clave “completa” la matriz completa de temperaturas,
//    en la segunda posición con clave “primavera” la matriz creada en el inciso h., 
//    y en la tercera posición con clave “invierno” la matriz creada en el inciso i.

/**
 * Summary of asociativo
 * @param array $matrizTemp
 * @param mixed $matrizInvierno
 * @param mixed $matrizPrim
 * @return void
 */
function asociativo ( array $matrizTemp, $matrizInvierno, $matrizPrim){

    $arregloAsociativo = array ();
    $arregloAsociativo = [
        "completa" => $matrizTemp,
        "primavera" => $matrizPrim,
        "invierno" => $matrizInvierno
    ];

}




// programa PRINCIPAL


$matrizTemp = [];
$matrizPrim = [];
$matrizInvierno = [];
$matrizAsociativa = [];
$opcion = -1;

do{

    echo "Menú de opciones:\n";
    echo "1: Carga automática de temperaturas\n";
    echo "2: Carga manual de temperaturas\n";
    echo "3: Mostrar matriz por filas y columnas\n";
    echo "4: Consultar temperatura por año y mes\n";
    echo "5: Consultar para un determinado año, las temperaturas de todos los meses\n";
    echo "6: Consultar temperaturas de un mes y promedio\n";
    echo "7: Mostrar temperaturas máximas y mínimas\n";
    echo "8: Crear y mostrar datos de primavera\n";
    echo "9: Crear y mostrar datos de invierno\n";
    echo "10: Crear y mostrar un arreglo asociativo\n";
    echo "0: Salir\n";
    echo "Seleccione una opcion:\n";
    $opcion = trim(fgets(STDIN));

    switch ($opcion){
        case 1:
            tempAutomatica($matrizTemp);
            break;
        case 2:
            tempManual($matrizTemp);
            break;
        case 3:
            contenidoFila($matrizTemp);
            break;
        case 4:
            tempAnioMes($matrizTemp);
            break;
        case 5:
            mostrarTempMeses($matrizTemp);
            break;
        case 6:
            mostrarPromTemp($matrizTemp);
            break;
        case 7:
            tempMaxYMin($matrizTemp);
            break;
        case 8:
            primavera($matrizTemp, $matrizPrim);
            break;
        case 9:
            invierno($matrizTemp, $matrizInvierno);
            break;
        case 0:
            echo "SALIR\n";
            break;
        default:
            echo "Opción inválida.\n";
    }

}while ($opcion != 0);






?>  
