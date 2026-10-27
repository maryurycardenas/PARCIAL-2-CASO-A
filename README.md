<img width="1536" height="1024" alt="Maraavillosa_ viaje brillante y glamuroso" src="https://github.com/user-attachments/assets/bab6d853-788e-452c-8a09-c85ec9667d6c" />

# PARCIAL-2-CASO-A
Trabajo Académico
Creado Usando Ayuda de IA

NOMBRE DE LA EMPRESA: Maraavillosa

Maraavillosa es una agencia de viajes creada Y enfocada en ofrecer experiencias de viaje seguras, cómodas y memorables. 

Eslogan: Viaja segura, explora sin límites.

MISIÓN
En Maraavillosa nos dedicamos a crear experiencias de viaje pensadas PARA TODO PUBLICO, ofreciendo planes vacacionales seguros, cómodos y accesibles. Buscamos que cada viajera pueda conocer nuevos destinos, disfrutar de nuevas experiencias y crear recuerdos inolvidables, brindándole un servicio cercano, confiable y adaptado a sus necesidades

VISIÓN
Para el año 2030, Maraavillosa busca convertirse en una agencia de viajes reconocida en Colombia por ofrecer experiencias turísticas destacándose por la seguridad, la calidad de sus servicios y la confianza que brinda a sus clientes, mientras amplía sus destinos y fortalece una comunidad de mujeres que disfrutan viajar y descubrir el mundo.

codigo visual
import java.awt.Desktop;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.time.LocalDate;
import java.time.LocalTime;
import java.util.Scanner;

public class MaaravillosaAgencia {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean sistemaActivo = true;

        System.out.println("=== BIENVENIDO A LA AGENCIA DE VIAJES MAARAVILLOSA ===");
        System.out.println("Tu seguridad es nuestro viaje. Turismo seguro para todo público.");

        // Bucle while principal para mantener el sistema continuo
        while (sistemaActivo) {
            String nombreCliente = "";
            String cedula = "";
            String fechaViaje = "";
            String destino = "";
            String tipoMaleta = "";
            double costoMaleta = 0.0;
            String nombreMaleta = "";
            int acompanantes = 0;
            double valorTotalViaje = 0.0;
            boolean facturaActiva = true;

            // Bucle secundario del menú interactivo con switch de 7 casos
            while (facturaActiva) {
                System.out.println("\n--- MENÚ PRINCIPAL DE RESERVA ---");
                System.out.println("1. Registrar Cliente (Nombre, Cédula, Fecha, Destino)");
                System.out.println("2. Tipo de maleta (MB: 285,325 COP / MP: 325,650 COP)");
                System.out.println("3. Acompañantes (Número entero)");
                System.out.println("4. Valor del viaje");
                System.out.println("5. Visualizar información en pantalla");
                System.out.println("6. Generar respaldo TXT y abrir Bloc de Notas");
                System.out.println("7. Salir y finalizar con palabra clave");
                System.out.print("Seleccione una opción del menú (1-7): ");

                if (!scanner.hasNextInt()) {
                    System.out.println("Error: Debe ingresar un número entero válido entre 1 y 7.");
                    scanner.next();
                    continue;
                }

                int opcion = scanner.nextInt();
                scanner.nextLine();

                switch (opcion) {
                    case 1:
                        System.out.print("Ingrese el nombre de la cliente/viajera (Solo letras): ");
                        String ingresoNombre = scanner.nextLine();
                        
                        if (ingresoNombre.matches(".*\\d.*")) {
                            System.out.println("Error: El nombre no puede contener números. Intente nuevamente.");
                        } else if (ingresoNombre.trim().isEmpty()) {
                            System.out.println("Error: El nombre no puede estar vacío.");
                        } else {
                            nombreCliente = ingresoNombre;
                            System.out.print("Ingrese número de cédula: ");
                            cedula = scanner.nextLine();
                            System.out.print("Ingrese la fecha del viaje (DD/MM/AAAA): ");
                            fechaViaje = scanner.nextLine();
                            System.out.print("Ingrese el destino vacacional: ");
                            destino = scanner.nextLine();
                            System.out.println("¡Datos registrados con éxito bajo la Ley 1581 de protección de datos!");
                        }
                        break;

                    case 2:
                        System.out.print("Ingrese el tipo de maleta (MB para Básica / MP para Premium): ");
                        tipoMaleta = scanner.nextLine().trim().toUpperCase();
                        
                        if (tipoMaleta.equals("MB")) {
                            costoMaleta = 285325.0;
                            nombreMaleta = "Maleta Basica";
                            System.out.println("Maleta Básica seleccionada: 285,325 COP");
                        } else if (tipoMaleta.equals("MP")) {
                            costoMaleta = 325650.0;
                            nombreMaleta = "Maleta Premium";
                            System.out.println("Maleta Premium seleccionada: 325,650 COP");
                        } else {
                            System.out.println("Opción inválida. Debe ingresar estrictamente 'MB' o 'MP'.");
                            tipoMaleta = "";
                            costoMaleta = 0.0;
                            nombreMaleta = "";
                        }
                        break;

                    case 3:
                        System.out.print("Ingrese la cantidad de acompañantes (Número entero estricto): ");
                        if (scanner.hasNextInt()) {
                            acompanantes = scanner.nextInt();
                            scanner.nextLine();
                            
                            if (acompanantes < 0) {
                                System.out.println("Error: La cantidad de acompañantes no puede ser negativa.");
                                acompanantes = 0;
                            } else {
                                System.out.println("Acompañantes registrados exitosamente: " + acompanantes);
                            }
                        } else {
                            System.out.println("Error: Debe ingresar obligatoriamente un número entero.");
                            scanner.next();
                        }
                        break;

                    case 4:
                        if (costoMaleta > 0 && acompanantes >= 0) {
                            valorTotalViaje = costoMaleta * acompanantes;
                            System.out.println("Valor total del viaje calculado: $ " + valorTotalViaje + " COP");
                        } else {
                            System.out.println("Aviso: Faltan datos previos (seleccione maleta y acompañantes).");
                        }
                        break;

                    case 5:
                        System.out.println("\n==========================================");
                        System.out.println("      FACTURA - AGENCIA MAARAVILLOSA      ");
                        System.out.println("==========================================");
                        System.out.println("Cliente: " + nombreCliente);
                        System.out.println("Cedula: " + cedula);
                        System.out.println("Fecha del Viaje: " + fechaViaje);
                        System.out.println("Destino: " + destino);
                        if (!nombreMaleta.isEmpty()) {
                            System.out.println(nombreMaleta + ": " + acompanantes + " x $ " + costoMaleta + " = $ " + valorTotalViaje + " COP");
                        }
                        System.out.println("Total a Pagar: $ " + valorTotalViaje + " COP");
                        System.out.println("==========================================");
                        break;

                    case 6:
                        // Respaldo automático en TXT con apertura en Bloc de Notas
                        try {
                            String nombreArchivo = "Respaldo_Factura_Maaravillosa.txt";
                            FileWriter escritor = new FileWriter(nombreArchivo);
                            escritor.write("==========================================\n");
                            escritor.write("   FACTURA OFICIAL - AGENCIA MAARAVILLOSA   \n");
                            escritor.write("==========================================\n");
                            escritor.write("Cliente: " + nombreCliente + "\n");
                            escritor.write("Cédula: " + cedula + "\n");
                            escritor.write("Fecha de Viaje: " + fechaViaje + "\n");
                            escritor.write("Destino: " + destino + "\n");
                            if (!nombreMaleta.isEmpty()) {
                                escritor.write(nombreMaleta + ": " + acompanantes + " x $ " + costoMaleta + " = $ " + valorTotalViaje + " COP\n");
                            }
                            escritor.write("Valor Total a Pagar: $ " + valorTotalViaje + " COP\n");
                            escritor.write("Fecha: " + LocalDate.now() + "\n");
                            escritor.write("Hora: " + LocalTime.now() + "\n");
                            escritor.write("==========================================\n");
                            escritor.close();
                            
                            System.out.println("¡Respaldo TXT generado con éxito!");

                            File archivoTxt = new File(nombreArchivo);
                            if (Desktop.isDesktopSupported()) {
                                Desktop.getDesktop().open(archivoTxt);
                                System.out.println("Abriendo archivo en el Bloc de Notas...");
                            }
                        } catch (IOException e) {
                            System.out.println("Error crítico al generar o abrir el archivo TXT.");
                        }
                        break;

                    case 7:
                        // Salir de la factura actual y exigir la palabra clave "vacaciones"
                        System.out.println("Finalizando la factura actual...");
                        facturaActiva = false;
                        break;

                    default:
                        System.out.println("Opción no válida. Elija un número del 1 al 7.");
                        break;
                }
            }

            // Validación de la palabra clave "vacaciones" requerida por el profesor
            System.out.print("\nPara cerrar completamente el sistema escriba la palabra 'vacaciones' (o presione Enter para atender otra factura): ");
            String palabraClave = scanner.nextLine();
            
            if (palabraClave.equalsIgnoreCase("vacaciones")) {
                sistemaActivo = false;
                System.out.println("Cierre total del sistema de ventas. ¡Gracias por preferir a Maaravillosa!");
            }
        }
        scanner.close();
    }
}

