# DartTallerNr1
void main() {
  ejercicio1();
  // Puedes añadir los siguientes ejercicios aquí a medida que los desarrolles:
  ejercicio2();
  ejercicio3();
  ejercicio4();
  ejercicio5();
  //ejercicio6();
}

void ejercicio1() {
  // Declaración de variables sobre la finca y la producción
  String nombreFinca = "Finca San Eduardo";
  int cajasCosechadas = 120;
  double precioPorCaja = 7.25;
  double costoTransportePorCaja = 0.50;

  // Cálculos de ingresos
  double ingresoBruto = cajasCosechadas * precioPorCaja;
  double costoTotalTransporte = cajasCosechadas * costoTransportePorCaja;
  double ingresoNeto = ingresoBruto - costoTotalTransporte;

  // Salida por consola con interpolación de variables
  print("=== RESULTADOS DEL EJERCICIO 1 ===");
  print("Finca: $nombreFinca");
  print("Cajas cosechadas: $cajasCosechadas");
  print("Precio por caja: \$${precioPorCaja.toStringAsFixed(2)} USD");
  print("Ingreso bruto: \$${ingresoBruto.toStringAsFixed(2)} USD");
  print("Costo de transporte ($costoTransportePorCaja USD/caja): \$${costoTotalTransporte.toStringAsFixed(2)} USD");
  print("Ingreso neto: \$${ingresoNeto.toStringAsFixed(2)} USD");
  print("----------------------------------");
}

/// Ejercicio 2: Recomendación de riego según la precipitación pluvial
/// Utiliza estructuras de control condicionales (if / else if / else)
void ejercicio2() {
  print("=== RESULTADOS DEL EJERCICIO 2 ===");
  
  // Lista de valores de prueba indicados en el ejercicio (10, 35 y 60 mm)
  List<double> nivelesLluvia = [10, 35, 60];

  for (double lluvia in nivelesLluvia) {
    String recomendacion = "";

    // Evaluación de rangos de lluvia
    if (lluvia > 50) {
      recomendacion = "Suspender riego";
    } else if (lluvia >= 20) {
      // Como ya descartamos los valores mayores a 50, aquí evaluamos el rango de 20 a 50
      recomendacion = "Riego reducido";
    } else {
      recomendacion = "Riego normal";
    }

    print("Precipitación: $lluvia mm  --->  Recomendación: $recomendacion");
  }
  
  print("----------------------------------");
}

void ejercicio3() {
  print("=== RESULTADOS DEL EJERCICIO 3 ===");

  // Lista de prueba con los cultivos solicitados y uno adicional para probar el default
  List<String> listaCultivos = ["banano", "cacao", "arroz", "pitahaya"];

  for (String cultivo in listaCultivos) {
    String frecuenciaCosecha = "";

    switch (cultivo.toLowerCase()) {
      case "banano":
        frecuenciaCosecha = "Cosecha semanal / quincenal continua durante todo el año.";
        break;
      case "cacao":
        frecuenciaCosecha = "Cosecha estacional / principal con recolección frecuente en época alta.";
        break;
      case "arroz":
        frecuenciaCosecha = "Cosecha anual de ciclo corto (aproximadamente a los 120-140 días de siembra).";
        break;
      default:
        frecuenciaCosecha = "Frecuencia de cosecha no definida en el sistema.";
        break;
    }

    print("Cultivo: ${cultivo.toUpperCase()}  --->  $frecuenciaCosecha");
  }

  print("----------------------------------");
}

void ejercicio4() {
  print("=== RESULTADOS DEL EJERCICIO 4 ===");

  List<int> cosechasSemana = [80, 95, 120, 60, 110, 90];
  
  int totalCajas = 0;
  int mayorValor = cosechasSemana[0];

  // Recorrido de la lista para sumar el total y hallar el mayor valor
  for (int i = 0; i < cosechasSemana.length; i++) {
    int cajas = cosechasSemana[i];
    totalCajas += cajas;

    if (cajas > mayorValor) {
      mayorValor = cajas;
    }
  }

  // Cálculo del promedio
  double promedioCajas = totalCajas / cosechasSemana.length;

  print("Registro semanal de cajas: $cosechasSemana");
  print("Total de cajas cosechadas: $totalCajas");
  print("Promedio diario de cajas: ${promedioCajas.toStringAsFixed(2)}");
  print("Mayor valor de cosecha: $mayorValor");

  print("\nDías con más de 100 cajas cosechadas:");
  for (int i = 0; i < cosechasSemana.length; i++) {
    if (cosechasSemana[i] > 100) {
      print(" - Día ${i + 1}: ${cosechasSemana[i]} cajas");
    }
  }

  print("----------------------------------");
}


// ---------------------------------------------------------
// FUNCIONES AUXILIARES PARA EL EJERCICIO 5
// ---------------------------------------------------------

/// Calcula el ingreso total multiplicando las cajas por el precio unitario.
double ingreso(int cajas, double precio) {
  return cajas * precio;
}

/// Función flecha que evalúa si la cosecha es buena (retorna true si cajas >= 100).
bool esBuenaCosecha(int cajas) => cajas >= 100;

/// Función de reporte con parámetros con nombre ({required, opcionales con valor por defecto}).
void reporte({required String finca, int cajas = 0}) {
  double precioUnitario = 7.25;
  double totalIngreso = ingreso(cajas, precioUnitario);
  bool calificacionCosecha = esBuenaCosecha(cajas);

  print("--- Reporte de Finca ---");
  print("Finca: $finca");
  print("Cajas cosechadas: $cajas");
  print("Ingreso calculado: \$${totalIngreso.toStringAsFixed(2)} USD");
  print("¿Es buena cosecha?: ${calificacionCosecha ? "Sí (≥ 100 cajas)" : "No (< 100 cajas)"}");
}

/// Ejercicio 5: Reporte con funciones (funciones, flecha y parámetros con nombre)
void ejercicio5() {
  print("=== RESULTADOS DEL EJERCICIO 5 ===");

  // Probando el reporte con diferentes fincas y volúmenes de cajas
  reporte(finca: "Finca San Eduardo", cajas: 120);
  print("");
  reporte(finca: "Finca La Esperanza", cajas: 75);
  print("");
  reporte(finca: "Finca El Paraíso"); // Usando el valor por defecto de cajas (0)

  print("----------------------------------");
}
