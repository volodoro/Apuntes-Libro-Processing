# Sintaxis para dibujar

Cuando dibujamos figuras primitivas, podemos asignarles colores y contorno. Para el color utilizamos fill(), donde los colores se escriben por defecto en valores de escala de grises o RGB entre 0 y 255 para cada uno. 
ADEMÁS PODEMOS AÑADIR UN SEGUNDO PARÁMETRO PARA CONTROLAR LA OPACIDAD, donde 255 hace que la figura sea completamente opaca y 0 que la figura sea totalmente transparente. Por ejemplo fill(122, 100). También 
podemos cambiar el grosor del contorno de las figuras utilizando stroke(), por ejemplo stroke(5).


Estas funciones pueden ser desactivadas utilizando noFill() para dibjugar una figura sin relleno y noStroke() para dibujar una figura sin contorno. Sin embargo, no se pueden utilizar ambas a la vez, ya que en 
caso de hacerlo, nada será dibujado en el lienzo.

También podemos utilizar la función smooth() para dibujar figuras con filtro antialiasing, el argumento que tome esta función (por ejemplo smooth(8) ) determinará qué tanto de ese filtro será aplicado a 
TODO LO QUE SE ENCUENTRE DEBAJO DE LA FUNCIÓN, al igual que fill() o stroke(). Si queremos dejar de utilizar smooth() en un determinado punto de nuestro código, utilizamos noSmooth().

## NOTA IMPORTANTE 

Al intentar utilizar la función smooth() en el siguiente código con el fin de eliminar el aliasing de algunas diagonales, me di cuenta de que cambiar el argumento de la función no producía ningún cambio en 
el dibujo final.
 Ante o que chatgpt me dijo:
 
Ojo: smooth(8) puede no estar haciendo nada (según renderer)

Tu sketch está usando el renderer por defecto (JAVA2D). En ese renderer, smooth(8) no siempre aplica (o se ignora el “8”). Si quieres control real del nivel de suavizado, usa P2D (o P3D):

``` processing
void setup() {
  size(640, 480, P2D);
  smooth(8);
}
```

Por esta razón incluí P2D en la función para crear el lienzo, luego de lo cual, el problema fue resuelto.


``` processing

void setup() {
  size(640, 480, P2D);
  smooth(8);
}

void draw() {

  background(255);
  fill(255, 0, 0, 30);
  stroke(0);
  strokeWeight(1);
  triangle(10, 10, 100, 30, 10, 100);
  quad(200, 200, 200, 300, 300, 350, 300, 230);
  quad(300, 350, 300, 230, 400, 210, 400, 320);
  triangle(200, 200, 300, 230, 400, 210 );
  fill(0, 200, 200, 10);
  rect(450, 100, 150, 350);
}
```

También podemos controlar los atributos de las líneas con strokeCap() y strokeJoin(). strokeCap puede recibir los argumentos ROUND, SQUARE o PROJECT. Mientras que strokeJoin() recibe los argumentos, BEVEL, 
MITER o ROUND. BEVEL, hace que los vértices de las figuras se unan en intersecciones cuadradas, MITER deja los vértices por default, y ROUND curva los vértices.

