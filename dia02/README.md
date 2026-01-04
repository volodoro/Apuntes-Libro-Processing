# PROGRAMACIÓN ORIENTADA A OBJETOS

La programación orientada a objetos es una manera de estructurar los códigos en "objetos", es decir, unidades de código que contienen TANTO DATOS COMO FUNCIONES. La función que vimos en e dia01 puede ser expan-
dida al hacerla parte de la definición de UNA CLASE.

## Los objetos son creados utilizando las clases como plantillas

Las variables para posicionar las lineas y establecer sus atributos de dibujo se mueven dentro de la definición de clase para estar más estrechamente asociadas con el dibujo de las lineas.

``` processing
Diagonals da, db; //da y db son variables que van a “apuntar” a objetos de esa clase. En este punto todavía no existen los objetos; solo declaraste los //nombres.

void setup() {
  size(100, 100);
  smooth();
  // Datos a ingresar (inputs) ---> x, y, velocidad, grosor, gris

  da = new Diagonals (0, 80, 1, 2, 0); //new Diagonals(...) construye un objeto en memoria. Lo que va dentro de los paréntesis son los argumentos que le //pasas al constructor de la clase.
  db = new Diagonals (0, 55, 2, 6, 255);
// Después, ese objeto se guarda en la variable da o db.
}

void draw() {
  background(204);
  da.update();
  db.update();
}

class Diagonals {
// Dentro de la clase declaras atributos (también llamados fields o variables de instancia).
//x, y: posición base del “grupo” de líneas, speed: cuánto avanza en X cada frame, thick: grosor del trazo,
//gray: color en escala de grises (0 = negro, 255 = blanco)
  int x, y, speed, thick, gray;

//El constructor: inicializa el objeto

/*Piensa que aquí ocurre esto:

Los parámetros (xPos, yPos, s, t, g) son los “inputs”.

Adentro, tú copias esos inputs a los atributos del objeto (x, y, etc.).

Con tus dos objetos:

da queda con: x=0, y=80, speed=1, thick=2, gray=0

db queda con: x=0, y=55, speed=2, thick=6, gray=255*/

 Diagonals(int xPos, int yPos, int s, int t, int g) {
    x = xPos;
    y = yPos;
    speed = s;
    thick = t;
    gray = g;
  }

//update(): comportamiento por frame

/*a) Estilo del dibujo

strokeWeight(thick); usa el grosor guardado en ese objeto.

stroke(gray); usa el gris guardado en ese objeto.

Por eso da dibuja fino y negro, y db grueso y blanco.

b) Dibuja 3 líneas diagonales

Las líneas se dibujan con coordenadas relativas a x y y:

Primera: desde (x, y) hasta (x+20, y-40)

Segunda: desde (x+10, y) hasta (x+30, y-40)

Tercera: desde (x+20, y) hasta (x+40, y-40)

Eso genera como una “peineta” de diagonales que se mueve.

c) Movimiento

x = x + speed;
Cada frame, x aumenta.
Como db.speed = 2, db se mueve el doble de rápido que da.*/
void update() {
  strokeWeight(thick);
  stroke(gray);
  line(x, y, x + 20, y - 40);
  line(x + 10, y, x + 30, y- 40);
  line(x + 20, y, x + 40, y - 40);
  x = x + speed;
  if (x > 100){
    x = -100;
  }
}

}
/**Este código demuestra esto:

Clase = definición (datos + funciones)

Objeto = una instancia con valores propios

En draw(), llamas el mismo método (update) sobre dos objetos diferentes,
y cada uno se comporta distinto por sus atributos./
```
