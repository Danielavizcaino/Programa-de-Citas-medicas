# Programa-de-Citas-medicas centro Medico Moderno
#include <iostream>
#include <string>
#include <vector>

using namespace std;

struct Medico {
    string nombre;
    string especialidad;
};

struct Paciente {
    string nombre;
    int edad;
};

struct Cita {
    Paciente paciente;
    Medico medico;
    string fecha;
    string hora;
};

vector<Cita> citas;

void programarCita(Paciente paciente, Medico medico, string fecha, string hora) {
    Cita nuevaCita;
    nuevaCita.paciente = paciente;
    nuevaCita.medico = medico;
    nuevaCita.fecha = fecha;
    nuevaCita.hora = hora;
    citas.push_back(nuevaCita);
    cout << "¡Cita programada exitosamente!" << endl;
}

int main() {
    cout << "Bienvenido al sistema de citas médicas" << endl;

    // Crear un médico de ejemplo
    Medico medico1 = {"Dr. vizcaino", "Cardiología"};

    // Solicitar al paciente ingresar su nombre y edad
    string nombrePaciente;
    int edadPaciente;
    cout << "Ingrese su nombre: ";
    getline(cin, nombrePaciente);
    cout << "Ingrese su edad: ";
    cin >> edadPaciente;
    cin.ignore(); // Limpiar el buffer de entrada

    // Crear un objeto Paciente
    Paciente paciente1 = {nombrePaciente, edadPaciente};

    // Solicitar fecha y hora para la cita
    string fechaCita, horaCita;
    cout << "Ingrese la fecha de la cita (YYYY-MM-DD): ";
    getline(cin, fechaCita);
    cout << "Ingrese la hora de la cita (HH:MM): ";
    getline(cin, horaCita);

    // Programar la cita
    programarCita(paciente1, medico1, fechaCita, horaCita);

    // Mostrar las citas programadas
    cout << "\nCitas programadas:\n";
    for (const auto& cita : citas) {
        cout << "Paciente: " << cita.paciente.nombre << endl;
        cout << "Médico: " << cita.medico.nombre << " (" << cita.medico.especialidad << ")" << endl;
        cout << "Fecha: " << cita.fecha << " Hora: " << cita.hora << endl << endl;
    }

    return 0;
}

