<div align="center">
  <a href="#-readme-in-english">🇺🇸 English</a> | 
  <a href="#-readme-en-español">🇪🇸 Español</a>
</div>

---

# 🇺🇸 README in English

# ♠️ BlackJack Game - JavaFX Edition

![Java](https://img.shields.io/badge/Java-22-orange?style=flat-square&logo=java)
![JavaFX](https://img.shields.io/badge/JavaFX-22.0.1-blue?style=flat-square&logo=oracle)
![Maven](https://img.shields.io/badge/Maven-Build-red?style=flat-square&logo=apache-maven)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

A complete implementation of the classic casino game **Blackjack** with a modern graphical interface developed in JavaFX. The project applies solid **Object-Oriented Programming** principles and design patterns to ensure clean, scalable, and maintainable code.

---

## 📋 Features

- 🎮 **Interactive graphical interface** with JavaFX
- 👤 **User system** with authentication and JSON persistence
- 💰 **Balance and betting management** in real-time
- 🃏 **Multiple deck system** (5 decks of 52 cards)
- 🎲 **Complete Blackjack logic** with standard rules
- 🏆 **Ranking system** to track best games
- 🎨 **Custom visual assets** for all cards

---

## 🏗️ Architecture and Design

The project follows an **MVC (Model-View-Controller)** architecture and applies fundamental OOP principles:

### **Domain Model**

#### 🃏 **Cards**
- **`Carta`**: Represents an individual card with suit and rank
- **`Mano`**: Manages a player's card collection with logic to calculate values (special Ace handling)
- **`Mazo`**: Manages 5 shuffled decks with 260 total cards

#### 👥 **Players (Inheritance and Polymorphism)**
```
ActorBlackjack (Abstract Class)
    ├── Jugador (implements I_ConSaldo)
    └── Croupier
```

- **`ActorBlackjack`**: Abstract base class that defines common behavior for all participants
- **`Jugador`**: Extends `ActorBlackjack` and implements `I_ConSaldo` to manage bets and balance
- **`Croupier`**: Extends `ActorBlackjack` with dealer-specific logic (rule of 17)

#### 👤 **Users**
- **`Usuario`**: Implements `I_ConSaldo` for account and balance management
- **`InicioSesion`**: Handles authentication and validations

#### 🎮 **Game**
- **`ManejoPartida`**: Orchestrates game flow and determines winners

#### 💾 **Persistence**
- **`GestionJSON`**: Abstraction for reading/writing users and bets in JSON format

### **Applied OOP Principles**

| Principle | Implementation |
|-----------|----------------|
| **Encapsulation** | Private attributes with validated getters/setters |
| **Inheritance** | `ActorBlackjack` as base for `Jugador` and `Croupier` |
| **Polymorphism** | `I_ConSaldo` interface implemented by `Usuario` and `Jugador` |
| **Abstraction** | Abstract class `ActorBlackjack` defines base contract |
| **Interfaces** | `I_ConSaldo` defines common behavior for monetary management |

### **Controllers (MVC)**
- `LoginController`: System access management
- `MainMenuController`: Main navigation
- `DesarrolloPartidaController`: Real-time game logic
- `IniciarSesionController` / `RegistrarseController`: User authentication

---

## 🚀 Installation and Execution

### **Prerequisites**
- **Java JDK 22** or higher
- **Maven 3.8+**
- JavaFX SDK 22.0.1 (included in dependencies)

### **Option 1: Run with Maven**
```bash
# Clone the repository
git clone <repository-url>
cd BlackJack

# Compile the project
mvn clean install

# Run the application
mvn javafx:run
```

### **Option 2: Run with Maven Wrapper (without Maven installed)**
```bash
# On Windows
.\mvnw.cmd clean javafx:run

# On Linux/Mac
./mvnw clean javafx:run
```

### **Option 3: Compile executable JAR**
```bash
mvn clean package
java -jar target/TP_Final-BlackJack_JavaFX-1.0-SNAPSHOT.jar
```

---

## 📂 Project Structure

```
src/main/java/
├── app/
│   └── App.java                      # Application entry point
├── controller/                       # MVC Controllers
│   ├── LoginController.java
│   ├── MainMenuController.java
│   └── DesarrolloPartidaController.java
├── model/
│   ├── clases/
│   │   ├── Cartas/                  # Carta, Mano, Mazo
│   │   ├── Jugadores/               # ActorBlackjack, Jugador, Croupier
│   │   ├── Usuario/                 # Usuario, InicioSesion
│   │   ├── Partida/                 # ManejoPartida
│   │   ├── Ranking/                 # Betting system
│   │   └── GestionJSON/             # Data persistence
│   ├── enums/
│   │   ├── PaloCarta.java
│   │   └── RangoCarta.java
│   ├── interfaces/
│   │   └── I_ConSaldo.java
│   └── exepciones/                  # Custom exceptions
└── path/
    └── Utiles.java                   # Constants and utilities

src/main/resources/
├── *.fxml                            # JavaFX views
├── *.css                             # Custom styles
└── assets/
    ├── cartas/                       # 52 card images + back
    └── *.jpg                         # Backgrounds and logos
```

---

## 🎮 How to Play

1. **Register or Sign In** with your credentials
2. **Add balance** to your account
3. **Place a bet** before starting
4. Receive your **2 initial cards** (the dealer also receives 2)
5. Decide to **hit** or **stand**
6. The dealer plays automatically (rule of 17)
7. Whoever gets closest to **21 without busting** wins

---

## 🛠️ Technologies Used

- **Java 22**: Primary language
- **JavaFX 22.0.1**: Modern UI framework
- **Maven**: Dependency and build management
- **org.json 20240303**: JSON processing library
- **ControlsFX**: Additional UI components
- **JUnit 5**: Testing framework (prepared)

---

## 🔧 Troubleshooting

### Error: "package org.json does not exist"
If you encounter compilation errors related to `org.json`, make sure your `pom.xml` includes the dependency:
```xml
<dependency>
    <groupId>org.json</groupId>
    <artifactId>json</artifactId>
    <version>20240303</version>
</dependency>
```
Then run:
```bash
mvn clean install
```

### Application won't start
Verify that you have Java JDK 22 installed:
```bash
java -version
```

---

## 📝 Implemented Blackjack Rules

✅ 260-card deck (5 standard decks)  
✅ Card values: 2-10 (face value), J/Q/K (10), A (1 or 11)  
✅ Natural blackjack (21 with 2 cards)  
✅ Dealer must hit until reaching 17  
✅ Automatic Ace value management  

---

## 🤝 Contributions

Contributions are welcome. Please:
1. Fork the project
2. Create a branch for your feature (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## 📄 License

This project is under the MIT License. See the `LICENSE` file for more details.

---

## 👨‍💻 Author

Developed with ☕ and passion for object-oriented programming.

---

## 🔮 Future Improvements

- [ ] Implement simultaneous multiplayer system
- [ ] Add card animations
- [ ] Advanced achievements and statistics system
- [ ] Game mode with different Blackjack variants
- [ ] Integration with relational database (MySQL/PostgreSQL)
- [ ] Complete unit testing with JUnit 5

---

# 🇪🇸 README en Español

# ♠️ BlackJack Game - JavaFX Edition

![Java](https://img.shields.io/badge/Java-22-orange?style=flat-square&logo=java)
![JavaFX](https://img.shields.io/badge/JavaFX-22.0.1-blue?style=flat-square&logo=oracle)
![Maven](https://img.shields.io/badge/Maven-Build-red?style=flat-square&logo=apache-maven)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

Una implementación completa del clásico juego de casino **Blackjack** con interfaz gráfica moderna desarrollada en JavaFX. El proyecto aplica principios sólidos de **Programación Orientada a Objetos** y patrones de diseño para garantizar un código limpio, escalable y mantenible.

---

## 📋 Características

- 🎮 **Interfaz gráfica interactiva** con JavaFX
- 👤 **Sistema de usuarios** con autenticación y persistencia en JSON
- 💰 **Gestión de saldo y apuestas** en tiempo real
- 🃏 **Sistema de múltiples mazos** (5 mazos de 52 cartas)
- 🎲 **Lógica de Blackjack completa** con reglas estándar
- 🏆 **Sistema de ranking** para llevar registro de las mejores partidas
- 🎨 **Assets visuales personalizados** para todas las cartas

---

## 🏗️ Arquitectura y Diseño

El proyecto sigue una arquitectura **MVC (Model-View-Controller)** y aplica principios fundamentales de POO:

### **Modelo de Dominio**

#### 🃏 **Cartas**
- **`Carta`**: Representa una carta individual con palo y rango
- **`Mano`**: Gestiona la colección de cartas de un jugador con lógica para calcular valores (manejo especial de Ases)
- **`Mazo`**: Administra 5 mazos barajados con 260 cartas totales

#### 👥 **Jugadores (Herencia y Polimorfismo)**
```
ActorBlackjack (Clase Abstracta)
    ├── Jugador (implementa I_ConSaldo)
    └── Croupier
```

- **`ActorBlackjack`**: Clase abstracta base que define el comportamiento común de todos los participantes
- **`Jugador`**: Extiende `ActorBlackjack` e implementa `I_ConSaldo` para gestionar apuestas y saldo
- **`Croupier`**: Extiende `ActorBlackjack` con lógica específica del dealer (regla del 17)

#### 👤 **Usuarios**
- **`Usuario`**: Implementa `I_ConSaldo` para gestión de cuenta y saldo
- **`InicioSesion`**: Maneja autenticación y validaciones

#### 🎮 **Partida**
- **`ManejoPartida`**: Orquesta el flujo del juego y determina ganadores

#### 💾 **Persistencia**
- **`GestionJSON`**: Abstracción para lectura/escritura de usuarios y apuestas en formato JSON

### **Principios de POO Aplicados**

| Principio | Implementación |
|-----------|----------------|
| **Encapsulamiento** | Atributos privados con getters/setters validados |
| **Herencia** | `ActorBlackjack` como base para `Jugador` y `Croupier` |
| **Polimorfismo** | Interfaz `I_ConSaldo` implementada por `Usuario` y `Jugador` |
| **Abstracción** | Clase abstracta `ActorBlackjack` define contrato base |
| **Interfaces** | `I_ConSaldo` define comportamiento común de gestión monetaria |

### **Controladores (MVC)**
- `LoginController`: Gestión de acceso al sistema
- `MainMenuController`: Navegación principal
- `DesarrolloPartidaController`: Lógica del juego en tiempo real
- `IniciarSesionController` / `RegistrarseController`: Autenticación de usuarios

---

## 🚀 Instalación y Ejecución

### **Prerrequisitos**
- **Java JDK 22** o superior
- **Maven 3.8+**
- JavaFX SDK 22.0.1 (incluido en las dependencias)

### **Opción 1: Ejecutar con Maven**
```bash
# Clonar el repositorio
git clone <repository-url>
cd BlackJack

# Compilar el proyecto
mvn clean install

# Ejecutar la aplicación
mvn javafx:run
```

### **Opción 2: Ejecutar con Maven Wrapper (sin Maven instalado)**
```bash
# En Windows
.\mvnw.cmd clean javafx:run

# En Linux/Mac
./mvnw clean javafx:run
```

### **Opción 3: Compilar JAR ejecutable**
```bash
mvn clean package
java -jar target/TP_Final-BlackJack_JavaFX-1.0-SNAPSHOT.jar
```

---

## 📂 Estructura del Proyecto

```
src/main/java/
├── app/
│   └── App.java                      # Punto de entrada de la aplicación
├── controller/                       # Controladores MVC
│   ├── LoginController.java
│   ├── MainMenuController.java
│   └── DesarrolloPartidaController.java
├── model/
│   ├── clases/
│   │   ├── Cartas/                  # Carta, Mano, Mazo
│   │   ├── Jugadores/               # ActorBlackjack, Jugador, Croupier
│   │   ├── Usuario/                 # Usuario, InicioSesion
│   │   ├── Partida/                 # ManejoPartida
│   │   ├── Ranking/                 # Sistema de apuestas
│   │   └── GestionJSON/             # Persistencia de datos
│   ├── enums/
│   │   ├── PaloCarta.java
│   │   └── RangoCarta.java
│   ├── interfaces/
│   │   └── I_ConSaldo.java
│   └── exepciones/                  # Excepciones personalizadas
└── path/
    └── Utiles.java                   # Constantes y utilidades

src/main/resources/
├── *.fxml                            # Vistas JavaFX
├── *.css                             # Estilos personalizados
└── assets/
    ├── cartas/                       # 52 imágenes de cartas + dorso
    └── *.jpg                         # Fondos y logos
```

---

## 🎮 Cómo Jugar

1. **Registrarse o Iniciar Sesión** con tus credenciales
2. **Agregar saldo** a tu cuenta
3. **Realizar una apuesta** antes de comenzar
4. Recibe tus **2 cartas iniciales** (el croupier también recibe 2)
5. Decide **pedir carta** o **plantarse**
6. El croupier juega automáticamente (regla del 17)
7. Gana quien se acerque más a **21 sin pasarse**

---

## 🛠️ Tecnologías Utilizadas

- **Java 22**: Lenguaje principal
- **JavaFX 22.0.1**: Framework de UI moderna
- **Maven**: Gestión de dependencias y build
- **org.json 20240303**: Librería para procesamiento JSON
- **ControlsFX**: Componentes UI adicionales
- **JUnit 5**: Testing (framework preparado)

---

## 🔧 Solución de Problemas

### Error: "package org.json does not exist"
Si encuentras errores de compilación relacionados con `org.json`, asegúrate de que el `pom.xml` incluya la dependencia:
```xml
<dependency>
    <groupId>org.json</groupId>
    <artifactId>json</artifactId>
    <version>20240303</version>
</dependency>
```
Luego ejecuta:
```bash
mvn clean install
```

### La aplicación no inicia
Verifica que tienes Java JDK 22 instalado:
```bash
java -version
```

---

## 📝 Reglas del Blackjack Implementadas

✅ Mazo de 260 cartas (5 mazos estándar)  
✅ Valores de cartas: 2-10 (valor nominal), J/Q/K (10), A (1 u 11)  
✅ Blackjack natural (21 con 2 cartas)  
✅ El croupier debe pedir hasta llegar a 17  
✅ Gestión automática del valor del As  

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor:
1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -m 'Agrega nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles.

---

## 👨‍💻 Autor

Desarrollado con ☕ y pasión por la programación orientada a objetos.

---

## 🔮 Futuras Mejoras

- [ ] Implementar sistema de múltiples jugadores simultáneos
- [ ] Agregar animaciones para las cartas
- [ ] Sistema de logros y estadísticas avanzadas
- [ ] Modo de juego con diferentes variantes de Blackjack
- [ ] Integración con base de datos relacional (MySQL/PostgreSQL)
- [ ] Testing unitario completo con JUnit 5
