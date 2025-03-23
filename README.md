# Investigación sobre Herencia en Programación Orientada a Objetos

## 1. Introducción
La herencia es un pilar fundamental de la Programación Orientada a Objetos (POO) que permite a una clase derivada (o hija) heredar atributos y métodos de una clase base (o padre). Esto fomenta la reutilización de código y facilita la extensibilidad del sistema.

## 2. Tipos de Herencia

### a) Herencia Simple
Ocurre cuando una clase hereda de una única clase base.

### b) Herencia Múltiple
Una clase hereda de más de una clase base (no es soportada directamente en C#, pero se puede simular con interfaces).

### c) Herencia Multinivel
Una clase hereda de otra clase derivada, formando una cadena de herencia.

### d) Herencia Jerárquica
Varias clases derivadas heredan de una misma clase base.

### e) Herencia Híbrida
Es una combinación de dos o más tipos de herencia.

## 3. Ejemplos de Código en C#

### Ejemplo 1: Herencia Simple
```csharp
class Animal {
    public string Nombre { get; set; }
    public Animal(string nombre) {
        Nombre = nombre;
    }
    public virtual string HacerSonido() {
        return "Sonido genérico";
    }
}

class Perro : Animal {
    public Perro(string nombre) : base(nombre) { }
    public override string HacerSonido() {
        return "Ladrido";
    }
}

Perro miPerro = new Perro("Firulais");
Console.WriteLine(miPerro.HacerSonido());
```

### Ejemplo 2: Herencia Múltiple (mediante interfaces)
```csharp
interface IVolador {
    string Volar();
}

interface INadador {
    string Nadar();
}

class Pato : IVolador, INadador {
    public string Volar() {
        return "Estoy volando";
    }
    public string Nadar() {
        return "Estoy nadando";
    }
}

Pato pato = new Pato();
Console.WriteLine(pato.Volar());
Console.WriteLine(pato.Nadar());
```

### Ejemplo 3: Herencia Multinivel
```csharp
class Vehiculo {
    public virtual string Descripcion() {
        return "Vehículo genérico";
    }
}

class Coche : Vehiculo {
    public override string Descripcion() {
        return "Soy un coche";
    }
}

class Deportivo : Coche {
    public override string Descripcion() {
        return "Soy un coche deportivo";
    }
}

Deportivo miCoche = new Deportivo();
Console.WriteLine(miCoche.Descripcion());
```

### Ejemplo 4: Herencia Jerárquica
```csharp
class Persona {
    public string Nombre { get; set; }
    public Persona(string nombre) {
        Nombre = nombre;
    }
}

class Estudiante : Persona {
    public Estudiante(string nombre) : base(nombre) { }
    public string Estudiar() {
        return $"{Nombre} está estudiando";
    }
}

class Profesor : Persona {
    public Profesor(string nombre) : base(nombre) { }
    public string Ensenar() {
        return $"{Nombre} está enseñando";
    }
}

Estudiante estudiante = new Estudiante("Juan");
Profesor profesor = new Profesor("María");
Console.WriteLine(estudiante.Estudiar());
Console.WriteLine(profesor.Ensenar());
```

### Ejemplo 5: Herencia Híbrida (uso de interfaces y clases)
```csharp
class SerVivo {
    public bool EstaVivo() {
        return true;
    }
}

class Mamifero : SerVivo {
    public bool TienePelo() {
        return true;
    }
}

interface IAve {
    bool TienePlumas();
}

class Murcielago : Mamifero, IAve {
    public bool TienePlumas() {
        return true;
    }
    public bool EsMurcielago() {
        return true;
    }
}

Murcielago miMurcielago = new Murcielago();
Console.WriteLine(miMurcielago.EstaVivo());
Console.WriteLine(miMurcielago.TienePelo());
Console.WriteLine(miMurcielago.TienePlumas());
```
