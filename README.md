# **Trabajo1**
## ***Índice***
1. Mis expectativas antes de aprender POO. 
   Qué creía que iba a aprender y para que creía que iba a servir lo que iba a ver sobre este tema.
2. Qué he aprendido durante las dos unidades.
3. Los dos ejercicios de las prácticas que para mí han sido los más importantes.
Por qué han sido los ejercicios más importantes para mí y lo que aprendí con ellos.
4. Mis conclusiones en este momento sobre estas dos unidades: 
    1. Que aprendí realmente de estas dos unidades
    2. Qué utilidad le veo a lo que aprendí
    3. Lo más positivo que he adquirido en estas dos unidades
    4. Lo que menos me ha gustado de estas dos unidades

---
## ***1. Mis expectativas antes de aprender POO. Qué creía que iba a aprender y para que creía que iba a servir lo que iba a ver sobre este tema.***

>Mis expectativas antes de aprender **Programación Orientada a Objetos (POO)** eran muy buenas,ya que me gusta mucho
la programación visual y todo el tema relacionado con los objetos y crear objetos con funciones.

> Yo creía que iba a aprender a como crear programas más visuales, como por ejemplo programas con botones que tengan diferentes
funciones, programas con objetos visuales(círculos,cuadrados,...) que se puedan mover,etc.

> Yo creía que lo que iba a ver sobre este tema me iba a servir para saber crear pequeñas aplicaciones o programas con objetos
visuales y funcionales como por ejemplo un pequeño programa con botones los cuales me permitan crear objetos, borrar objetos que 
me lleven a otra parte de la aplicación,... .Otro ejemplo sería crear un programa que simule un juego de mesa con funciones básicas, como por ejemplo
hacer un parchís el cual se vea el tablero, se vean las fichas, que las fichas se muevan,etc.También el juego de la oca en el que se vean las fichas con dados que generen números aleatorios y se vean el número que han salido en los dados,etc.

---
## ***2. Qué he aprendido durante las dos unidades.***
>Durante las dos unidades he aprendido a como crear objetos, a crear métodos, a crear constructores, como funcionan las diferentes relaciones entre clases,
como funciona la herencia de clases,que atributos heredan las clases, que es una superclase, que es una subclase, saber diferenciarlas, saber que una clase puede superclase de una clase y
a su vez ser subclase de otra, saber que una clase por defecto tiene una superclase llamada ***Object*** de la cual heredan los métodos que esta tiene
que son los métodos **toString** y el **equals**, otra cosa que he aprendido es que un objeto puede tener un atributo cuyo tipo sea de otro objeto
que hayamos creado.También he aprendido cuáles son los tipos de atributos ***(public,private,protected y friendly)*** y las reglas de visibilidad de cada uno de ellos ,etc.


### Reglas de visibilidad:

|Zona |Private(Privado) | Sin modificador(Friendly) | Protected(Protegido)| Public(Público)|
|:---|:----|:----:| ----:| ----:|
|Misma clase| X| X | X | X |
|Subclase en el mismo paquete | | X | X | X |
|Clase (no subclase) en el mismo paquete| | X | X | X |
|Subclase en otro paquete | | | X | X |
|Clase (no subclase) en otro paquete| | | | X |

---
## ***3.Los dos ejercicios de las prácticas que para mí han sido los más importantes. Por qué han sido los ejercicios más importantes para mí y lo que aprendí con ellos.***
> Para mí uno de los ejercicios de las prácticas que ha sido de lo más importantes es la práctica 18, la de los Puntos.
Para mí es una de las prácticas más importantes porque aprendes a como crear objetos, crear métodos, aprendes a utilizar los métodos get y set
aprendes a crear atributos en una clase que son de tipo de objetos de otra clase, por ejemplo en este caso en la clase ***Rectangulo.java*** tiene un atributo llamado esquina que es de tipo Punto,etc.

> Con este ejercicio he aprendido como funcionan los métodos get y set, he aprendido a crear métodos como el de dibujar, también he aprendido con esta práctica que se pueden crear objetos de diferentes maneras mediante los diferentes constructores que hayamos creado, a como crear un punto y sus atributos,etc.

### Aquí tenemos el código de las clases java correspondientes a la Práctica18-Puntos:

#### Punto.java
```Java
public class Punto {
    private double x;
    private double y;

    public double getX() {
        return x;
    }

    public double getY() {
        return y;
    }

    public void setX(double x) {
        this.x = x;
    }

    public void setY(double y) {
        this.y = y;
    }
    public void cambiarCoords(double x, double y){
        this.x = x;
        this.y = y;
    }
    public Punto copia(){
        Punto p = new Punto();
        p.cambiarCoords(x, y);
        return p;
    }
    public boolean iguales(Punto p){
        return x == p.x && y == p.y;
    }
    public void sumaCoords(Punto p){
        x += p.x;
        y += p.y;
    }
    public double obtenerDistancia(Punto p){
        double dx = x - p.x;
        double dy = y - p.y;
        return Math.sqrt(dx*dx + dy*dy);
    }
}
```
#### Rectangulo.java
```Java
public class Rectangulo {
    private Punto esquina;
    private double anchura;
    private double altura;

    public void setAnchura(double anchura) {
        this.anchura = anchura;
    }

    public void setAltura(double altura) {
        this.altura = altura;
    }

    public void cambiarEsquina(double x, double y){
            esquina.cambiarCoords(x, y);
        }
    public void cambiarEsquina(Punto p){
        esquina = p;
    }

    public void dibujar(){
       for(int i=1; i<=altura; i++){
           for(int j=1; j<=anchura; j++){
               System.out.print("*");
           }
           System.out.println();
       }
    }

    public void dibujar(char c){
         for(int i=1; i<=altura; i++){
              for(int j=1; j<=anchura; j++){
                System.out.print(c);
              }
              System.out.println();
         }
    }

    public boolean interior(Punto p){
        return p.getX() >= esquina.getX() &&
               p.getX() <= esquina.getX() + anchura &&
               p.getY() >= esquina.getY() &&
                p.getY() <= esquina.getY() + altura;
    }

    public Punto[] vertices(){
        Punto[] p = new Punto[4];
        p[0] = esquina.copia();
        p[1] = new Punto();
        p[1].cambiarCoords(esquina.getX() + anchura, esquina.getY());
        p[2] = new Punto();
        p[2].cambiarCoords(esquina.getX() + anchura, esquina.getY() + altura);
        p[3] = new Punto();
        p[3].cambiarCoords(esquina.getX(), esquina.getY() + altura);
        return p;
    }


}
```

>La otra práctica que me ha parecido de las más importantes es la práctica 20, la de las Barajas.
Para mí esta es una de las prácticas más importantes porque aprendemos a utilizar el contructor por defecto, aprendemos a crear atributos estáticos, utilizamos cosas vistas anteriormente como el ***shuffle*** para poder barajar las cartas, aprendemos como funcionan y como crear atributos que son arrays de objetos , por ejemplo en la clase Baraja tenemos el atributo cartas que es un array de tipo Carta,etc. 

>Yo lo que he aprendido con esta práctica es como funcionan y como crear los constructores por defecto,también he aprendido a crear atributos que son arrays cuyo tipo es un objeto,en este caso tenemos el atributo cartas en la clase Baraja que es un array de cartas, y como usarlos.También he aprendido como utilizar los métodos que he creado y además como construir objetos sin tener que introducir ningún dato a la hora de crearlo.

### Aquí tenemos el código de las clases java correspondientes a la Práctica20-Barajas:

#### Baraja.java
```Java
public class Baraja {
    private Carta[] cartas;
    private int numCartas;
    private static final int NUM_PALOS = 4;
    private static final int NUM_CARTAS = 10;

    public Baraja() {
        cartas = new Carta[NUM_PALOS * NUM_CARTAS];
        numCartas = 0;
        for (int palo = 1; palo <= NUM_PALOS; palo++) {
            for (int valor = 1; valor <= NUM_CARTAS; valor++) {
                cartas[numCartas] = new Carta(palo, valor);
                numCartas++;
            }
        }
    }

    public void barajar() {
        for (int i = 0; i < 100; i++) {
            int pos1 = (int) (Math.random() * numCartas);
            int pos2 = (int) (Math.random() * numCartas);
            Carta aux = cartas[pos1];
            cartas[pos1] = cartas[pos2];
            cartas[pos2] = aux;
        }
    }


    public void escribe() {
        for (int i = 0; i < numCartas; i++) {
            cartas[i].escribe();
        }
    }
}
```
#### Carta.java
```Java
public class Carta {
    private int palo;
    private int valor;

    private static final int OROS=1;
    private static final int ESPADAS=2;
    private static final int BASTOS=3;
    private static final int COPAS=4;
    private static final int AS=1;
    private static final int SOTA=8;
    private static final int CABALLO=9;
    private static final int REY=10;

    private static final String[] PALOS = {"","Oros","Espadas","Bastos","Copas"};
    private static final String[] VALORES = {"","As","2","3","4","5","6","7","Sota","Caballo","Rey"};

    public Carta(int palo, int valor) {
        darValor(palo,valor);
    }

    public Carta(){
        darValor(Carta.OROS, Carta.AS);
    }

    public void darValor(int palo,int valor){
        this.valor = valor;
        this.palo = palo;
    }

    public void escribe(){
        System.out.println(VALORES[valor]+" de "+PALOS[palo]);
    }
}
```
#### App.java
```Java
public class App {
    public static void main(String[] args) throws Exception {
        Baraja baraja = new Baraja();
        baraja.escribe();
        System.out.println();
        System.out.println();
        baraja.barajar();
        baraja.escribe();
    }
}
```
---
## 4. Mis conclusiones en este momento sobre estas dos unidades:
### 4.1. Que aprendí realmente de estas dos unidades
>Lo que realmente aprendí de estas dos unidades es a como crear objetos, como crear métodos, como crear constructores, como funcionan las relaciones entre clases,
como funciona la herncia entre clases,como indicar a una clase que es heredada de otra, también aprendí a como crear clases estáticas y como funcionan y también a como crear interfaces y como implementarlas,etc.

### 4.2. Qué utilidad le veo a lo que aprendí
>La utilidad que le veo a lo que aprendí es que gracias al aprender a como crear objetos, además de como crear constructores y métodos, esto me sirve como base para poder empezar a crear programas más visuales y también a entender como funcionan.

### 4.3 Lo más positivo que he adquirido en estas dos unidades
>Lo más positivo que he adquirido en estas dos unidades es que he aprendido muchas cosas nuevas sobre la ***Programación Orientada a Objetos (POO)***, he aprendido como funcionan los objetos y que lo positivo de aprender esto es que me puede servir para crear programas relacionados con la ***Programación Orientada a Objetos (POO)*** en el futuro y a entenderlos y comprenderlos mejor.

### 4.4 Lo que menos me ha gustado de estas dos unidades
>Lo que menos me ha gustado de estas dos unidades fue que no hemos hecho ningún programa con algún elemento visual como un botón funcional, un objeto con funciones, un objeto (cuadrado,círculo,...) que se pueda mover,etc.

![](https://desarrolloweb.com/media/154/programacion-orientada-a-objetos.jpeg)



