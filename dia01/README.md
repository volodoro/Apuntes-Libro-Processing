
``` processing
background(0); //color del fondo en negro
stroke(255); //color de las líneas ---> blanco
strokeWeight(5); //grosor de las líneas 
line(10, 80, 30, 40);
line(20, 80, 40, 40);
line(30, 80, 50, 40);
line(40, 80, 60, 40);
line(50, 80, 70, 40);
```

Las funciones setup() y draw() permiten que el código corra de forma continua. Luego de cada ciclo de draw() se dibuja un fotograma.

El siguiente código suma 1 a la posición horizontal (es decir, la variable x) por cada fotograma, haciendo que cuando x = 100, el valor vuelva instantáneamente a -40. Esto se logra gracias a una estructura 
if, con la sintaxis

``` processing


if (condicion que quiero evaluar){
  acción que quiero que realice el código
  si la condición especificada SE CUMPLE
}

```
``` processing
int x = 0;
int y = 55;

void setup() {
  size(100,100); //tamaño del lienzo ---> 100 pixeles x 100 pixeles
  
  }
  
void draw() {
background(204);
line(x, y, x + 20, y - 40);
line(x + 10, y, x + 30, y- 40);
line(x + 20, y, x + 40, y - 40);

x = x + 1;


if (x > 100){
  x = -40;
}

}
```
El siguiente código asigna los valores horizontal (x) y vertical (y) al origen de las líneas según la posición del cursor utilizando las funciones mouseX y mouseY respectivamente.
``` processing

void setup() {
  size(100,100); //tamaño del lienzo ---> 100 pixeles x 100 pixeles
  
  }
  

  
void draw() {
  
    float x = mouseX;
  float y = mouseY;
background(204);
line(x, y, x + 20, y - 40);
line(x + 10, y, x + 30, y- 40);
line(x + 20, y, x + 40, y - 40);


}
```

## Funciones 

### Las funciones son un conjunto dentro de un programa que desarrollan una tarea en específico.

Por ejemplo, en el siguiente código, la función diagonals() está diseñada para dijar tres líneas paralelas en diagonal CON SOLO UNA LÍNEA DE CÓDIGO. Las funciones tienen PARÁMETROS (el grupo de números que
se escriben después del paréntesis con el nombre de la función), en este caso, la función necesita que se le especifiquen las posiciones para x e y de la línea izquierda.

``` processing
void setup() {
  size(100,100); //tamaño del lienzo ---> 100 pixeles x 100 pixeles
  noLoop(); //evita que processing ejecute el código dentro de draw() en bucle
  
  }
  

  
void draw() {
  
diagonals(40, 90);
diagonals(60, 62);
diagonals(20, 40);


}

void diagonals(int x, int y){ // se definen las variables que utilizará la función como argumentos dentro del paréntesis
line(x, y, x + 20, y - 40);
line(x + 10, y, x + 30, y- 40);
line(x + 20, y, x + 40, y - 40);

}
```


Si quisiéramos tener muchos elementos en pantalla, sin utilizar demasiadas variables, lo más conveniente en ese caso sería utilizar ARREGLOS. 

## Los arreglos pueden almacenar una lista de elementos bajo un mismo nombre

## Un CICLO FOR es muy útil para cumplir un ciclo por cada elemento del arreglo


``` processing

int num = 20;
int[] dx = new int[num];
int[] dy = new int[num];

void setup() {
  size(100, 100);
  for (int i = 0; i < num; i++) {
    dx[i] = i * 5; // Asigna posiciones en X separadas de a 5 píxeles:
    dy[i] = 12 + (i * 6); // Asigna posiciones en Y separadas de a 6 píxeles y con un "offset" de 12:
  }
}



void draw() {
  background(204);
  for (int i = 0; i < num; i++ ) { //Este ciclo recorre los 20 elementos y para cada uno hace 3 cosas:
    dx[i] = dx[i] + 1; // • Actualiza la posición X sumando un pixel de movimiento hacia la derecha por cada frame
    if (dx[i] > 100) {
      dx[i] = -100; // Reaparición cuando sale del borde: Si la X pasa 100, ya se salió por el lado derecho. Entonces se manda a -100 para que empiece fuera por la izquierda, y luego vuelva a entrar.
    }
    diagonals(dx[i], dy[i]);
  }
}

void diagonals(int x, int y) { // se definen las variables que utilizará la función como argumentos dentro del paréntesis

  line(x, y, x + 20, y - 40);
  line(x + 10, y, x + 30, y- 40);
  line(x + 20, y, x + 40, y - 40);
}

```
