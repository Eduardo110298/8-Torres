{
UNIVERSIDAD DE ORIENTE
NUCLEO NUEVA ESPARTA
ESCUELA DE INGENIERIA Y CIENCIAS APLICADAS
LICENCIATURA EN INFORMATICA
LENGUAJES DE PROGRAMACION

PROYECTO 4: Las 8 Torres.

REALIZADO POR:
Eduardo Manuel Rodriguez Lara
C.I.: 26.082.457

}
program proyecto;
{
A continuacion la seccion de tipos, en donde se crean los tipos de variables
para las matrices utilizadas en el programa.
}
 type
  matrizCoord = array[0..7,0..1] of integer; {Tipo: matrizCoord(Matriz de coordenadas)}
  tipomatriz = array[0..7,0..7] of integer;  {Tipo: tipomatriz(Matriz asociada al tablero)}
{
A continuacion la seccion de variables, donde se establecen las variables
globales utilizadas en el programa.
}
 var
  difFil,difCol:boolean;
  {
  Banderas que indican si las torres estan o no
  ubicadas en diferentes filas y en diferentes
  columnas.
  }
  matriz: tipomatriz; {La matriz que representa el tablero}
  coords: matrizCoord; {La matriz que representa las posiciones de las torres}
{
A continuacion la seccion de declaracion de funciones y procedimientos.
}
procedure inicializar;
{
Procedimiento que inicializa toda la matriz con ceros.
}
  var
    i,j:integer;
  begin
  for i:=0 to 7 do
      begin
        for j:=0 to 7 do
          begin
            matriz[i,j] := 0;
          end;
      end;
  end;

procedure posicionRandomInicial;
{
Procedimiento que se encarga de asignar las torres
a posiciones aleatorias a lo largo del tablero.
}
  var
    torre,i,j:integer;
    asignado:boolean;
  begin
  for torre:=1 to 8 do
    begin
      asignado:=false;
      while (asignado = false) do
        begin
          i:=random(7);
          j:=random(7);
          if (matriz[i,j]=0) then
            begin
              matriz[i,j]:=torre;
              coords[torre-1,0]:= i;
              coords[torre-1,1]:= j;
              asignado:=true;
            end;
        end;
    end;
  end;

procedure mostrarMatriz;
{
Procedimiento que se encarga de mostrar la matriz.
}
  var
    i,j:integer;
  begin
    for i:=0 to 7 do
      begin
        for j:=0 to 7 do
          begin
            if(matriz[i,j]=0)then
              begin
                write('__');
              end
            else
             begin
               write('T',matriz[i,j]);
             end;
            write(' ');
          end;
        writeln;
      end;
      writeln;
  end;
{
De aqui en adelante estan los metodos que me son utilizados
por el proceso ubicarPorFilas.
}
function sePuedeArriba(idTorre: integer): boolean;
  {
  Funcion que se encarga de decir si una torre dada
  puede moverse para arriba.
  }
    begin
      if (coords[idTorre-1,0]=0) then
        begin
          sePuedeArriba:= false;
        end
      else
        begin
          if (matriz[coords[idTorre-1,0]-1,coords[idTorre-1,1]] <> 0) then
            begin
              sePuedeArriba:= false;
            end
          else
            begin
              sePuedeArriba:= true;
            end
        end
    end;

  function sePuedeAbajo(idTorre: integer): boolean;
    {
    Funcion que se encarga de decir si una torre dada
    puede moverse hacia abajo.
    }
    begin
      if (coords[idTorre-1,0]=7) then
        begin
          sePuedeAbajo:= false;
        end
      else
        begin
          if (matriz[coords[idTorre-1,0]+1,coords[idTorre-1,1]] <> 0) then
            begin
              sePuedeAbajo:= false;
            end
          else
            begin
              sePuedeAbajo:= true;
            end
       end
    end;

  function isCleanAbove(idTorre: integer):boolean;
  {
    Funcion que se encarga de decir si la fila que esta
    arriba no tiene ninguna torre.
  }
    var
      i,filaSup: integer;
      isClean:boolean;
    begin
      filaSup:=coords[idTorre-1,0] - 1;
      isClean:=true;
      i:=0;
      while (isClean and (i<=7)) do
        begin
          if(coords[i,0]=filaSup)then
            isClean:=false;
          i:=i+1;
        end;
      isCleanAbove:=isClean;
    end;

  function isCleanUnder(idTorre: integer):boolean;
  {
    Funcion que se encarga de decir si la fila que esta
    abajo no tiene ninguna torre.
  }
    var
      i,filaInf: integer;
      isClean:boolean;
    begin
      filaInf:=coords[idTorre-1,0] + 1;
      isClean:=true;
      i:=0;
      while (isClean and (i<=7)) do
        begin
          if(coords[i,0]=filaInf)then
            isClean:=false;
          i:=i+1;
        end;
      isCleanUnder:=isClean;
    end;

  procedure difFilas(coords:matrizCoord);
  {
    Procedimiento que se encarga de verificar si todas
    las torres estan en diferentes filas. Actua sobre
    la bandera global difFil.
  }
    var
       i,j:integer;
       diferentes:boolean;
    begin
      i:=0;
      diferentes:=true;
      while(i<=6)do
       begin
         j:=i+1;
         while(diferentes and (j<=7))do
           begin
              if(coords[i,0]=coords[j,0])then
               begin
                diferentes:=False;
               end;
               j:=j+1;
           end;
           i:=i+1;
       end;
       difFil:=diferentes;
    end;

{
De aqui en adelante estan los metodos que me son utilizados
por el proceso ubicarPorColumnas.
}
 function sePuedeDerecha(idTorre: integer): boolean;
 {
  Funcion que se encarga de decir si una torre dada
  puede moverse hacia la derecha.
  }
    begin
      if (coords[idTorre-1,1]=7) then
        begin
          sePuedeDerecha:= false;
        end
      else
        begin
          if (matriz[coords[idTorre-1,0],coords[idTorre-1,1]+1] <> 0) then
            begin
              sePuedeDerecha:= false;
            end
          else
            begin
              sePuedeDerecha:= true;
            end
        end
    end;

  function sePuedeIzq(idTorre: integer): boolean;
  {
  Funcion que se encarga de decir si una torre dada
  puede moverse hacia la izquierda.
  }
    begin
      if (coords[idTorre-1,1]=0) then
        begin
          sePuedeIzq:= false;
        end
      else
        begin
          if (matriz[coords[idTorre-1,0],coords[idTorre-1,1]-1] <> 0) then
            begin
              sePuedeIzq:= false;
            end
          else
            begin
              sePuedeIzq:= true;
            end
       end
    end;

  function isCleanRigth(idTorre: integer):boolean;
  {
    Funcion que se encarga de decir si la fila que esta
    a la derecha no tiene ninguna torre.
  }
    var
      i,colDer: integer;
      isClean:boolean;
    begin
      colDer:=coords[idTorre-1,1] + 1;
      isClean:=true;
      i:=0;
      while (isClean and (i<=7)) do
        begin
          if(coords[i,1]=colDer)then
            isClean:=false;
          i:=i+1;
        end;
      isCleanRigth:=isClean;
    end;

  function isCleanLeft(idTorre: integer):boolean;
  {
    Funcion que se encarga de decir si la fila que esta
    a la izquierda no tiene ninguna torre.
  }
    var
      i,colIzq: integer;
      isClean:boolean;
    begin
      colIzq:=coords[idTorre-1,1] - 1;
      isClean:=true;
      i:=0;
      while (isClean and (i<=7)) do
        begin
          if(coords[i,1]=colIzq)then
            isClean:=false;
          i:=i+1;
        end;
      isCleanLeft:=isClean;
    end;

  procedure difColumnas(coords:matrizCoord);
  {
    Procedimiento que se encarga de verificar si todas
    las torres estan en diferentes columnas. Actua sobre
    la bandera global difCol.
  }
    var
       i,j:integer;
       diferentes:boolean;
    begin
      i:=0;
      diferentes:=true;
      while(i<=6)do
       begin
         j:=i+1;
         while(diferentes and (j<=7))do
           begin
              if(coords[i,1]=coords[j,1])then
               begin
                diferentes:=False;
               end;
               j:=j+1;
           end;
           i:=i+1;
       end;
       difCol:=diferentes;
    end;
{
A continuacion la declaracion del monitor.
El monitor en esta oportunidad me esta controlando el tablero.
Existen dos procesos que pueden tomar el tablero:
 -ubicarPorFilas
 -ubicarPorColumnas

Por lo tanto, el monitor posee dos procedimientos que son usados
por esos procesos:
 -tomarControl
 -liberarControl

Ambos procesos estan programados para que al inicio, deseen tomar el control,
y al final, cuando hayan terminado de realizar su tarea, procedan a liberar
el control sobre el tablero.

Es necesaria una variable booleana que indique si el tablero esta o no tomado
por algun proceso.

}
 monitor tablero;
   export tomarControl;
   export liberarControl;
   var
     tableroTomado:boolean;
     ocupado:condition;
   procedure tomarControl;
   {
   Procedimiento que consulta si el tablero esta tomado, y si lo esta
   entonces decide enviar a la cola al proceso que esta queriendo tomar
   el control. Si el tablero NO esta tomado, entonces simplemente se
   cambia el valor de tableroTomado a verdadero(true).
   }
     begin
      if (tableroTomado) then
        delay(ocupado);
      tableroTomado:=true;
     end;

   procedure liberarControl;
   {
   Procedimiento que se encarga de cambiar la bandera tableroTomado a
   falso y de desencolar al proceso que estuvo esperando a que el tablero
   estuviera disponible.
   }
     begin
       tableroTomado:=false;
       resume(ocupado);
     end;

   end;
{
Fin de la declaracion del monitor
}

{
A continuacion, la declaracion de los procesos que se encargan de
ubicar todas las torres en filas y columnas diferentes.
}
 process ubicarPorFilas(var coords:matrizCoord);
 {
   Proceso que se encarga de ubicar las torres en filas diferentes.
   Tal y como se menciona anteriormente, el proceso intenta tomar el
   control del tablero justo al inicio, y al finalizar libera el control.

   La logica del proceso consiste en que cada una de las torres busca una fila
   vacia a donde moverse. Si la encuentra, se mueve. El proceso continua hasta
   que ya todas esten en diferentes filas.

   Por cada una de las torres, se pregunta primero si se puede mover hacia arriba
   y si tambien la fila de arriba esta vacia,y si estas dos cosas resultan
   ciertas entonces se procede a mover la torre hacia la fila de arriba. Tambien
   se preguntan las mismas cosas para la fila de abajo (Si el movimiento es valido
   y si la fila esta vacia).

   Solo se mueve una torre si el movimiento la lleva a una fila vacia.
 }
    var
      idTorre: integer;
    begin
      tablero.tomarControl;
      difFilas(coords);
      while(not(difFil))do
        begin
          for idTorre:=1 to 8 do
            begin
              if (sePuedeArriba(idTorre) and isCleanAbove(idTorre)) then
                begin
                 matriz[coords[idTorre-1,0],coords[idTorre-1,1]]:=0;
                 matriz[coords[idTorre-1,0]-1,coords[idTorre-1,1]]:=idTorre;
                 coords[idTorre-1,0]:=coords[idTorre-1,0]-1;
                 writeln('Movimiento hacia arriba de T',idTorre,'!:');
                 mostrarMatriz;
                end
              else
                begin
                  if (sePuedeAbajo(idTorre) and isCleanUnder(idTorre)) then
                    begin
                     matriz[coords[idTorre-1,0],coords[idTorre-1,1]]:=0;
                     matriz[coords[idTorre-1,0]+1,coords[idTorre-1,1]]:=idTorre;
                     coords[idTorre-1,0]:=coords[idTorre-1,0]+1;
                     writeln('Movimiento hacia abajo de T',idTorre,'!:');
                     mostrarMatriz;
                    end;
                end;
            end;
          difFilas(coords);
        end;
        tablero.liberarControl;
    end;

 process ubicarPorColumnas(var coords:matrizCoord);
 {
   Proceso que se encarga de ubicar las torres en columnas diferentes.
   Tal y como se menciona anteriormente, el proceso intenta tomar el
   control del tablero justo al inicio, y al finalizar libera el control.

   La logica del proceso consiste en que cada una de las torres busca una columna
   vacia a donde moverse. Si la encuentra, se mueve. El proceso continua hasta
   que ya todas esten en diferentes columnas.

   Por cada una de las torres, se pregunta primero si se puede mover hacia la derecha
   y si tambien la columna de la derecha esta vacia,y si estas dos cosas resultan
   ciertas entonces se procede a mover la torre hacia la columna de la derecha. Tambien
   se preguntan las mismas cosas para la columna de la izquierda (Si el movimiento es
   valido y si la columna esta vacia).

   Solo se mueve una torre si el movimiento la lleva a una columna vacia.
 }
    var
      idTorre: integer;
    begin
      tablero.tomarControl;
      difColumnas(coords);
      while(not(difCol))do
        begin
          for idTorre:=1 to 8 do
            begin
              if (sePuedeDerecha(idTorre) and isCleanRigth(idTorre)) then
                begin
                 matriz[coords[idTorre-1,0],coords[idTorre-1,1]]:=0;
                 matriz[coords[idTorre-1,0],coords[idTorre-1,1]+1]:=idTorre;
                 coords[idTorre-1,1]:=coords[idTorre-1,1]+1;
                 writeln('Movimiento hacia la derecha de T',idTorre,'!:');
                 mostrarMatriz;
                end
              else
                begin
                  if (sePuedeIzq(idTorre) and isCleanLeft(idTorre)) then
                    begin
                     matriz[coords[idTorre-1,0],coords[idTorre-1,1]]:=0;
                     matriz[coords[idTorre-1,0],coords[idTorre-1,1]-1]:=idTorre;
                     coords[idTorre-1,1]:=coords[idTorre-1,1]-1;
                     writeln('Movimiento hacia la izquierda de T',idTorre,'!:');
                     mostrarMatriz;
                    end;
                end;
            end;
          difColumnas(coords);
        end;
        tablero.liberarControl;
    end;
{
Inicio del algoritmo principal.
}
 begin
   inicializar;           {Se inicializa la matriz}
   posicionRandomInicial; {Se ubican las torres en posiciones aleatorias}
   writeln('Matriz Inicial: ');
   mostrarMatriz;
   {
   Inicio de la seccion para los procesos de forma concurrente.
   }
   cobegin
     ubicarPorFilas(coords);
     ubicarPorColumnas(coords);
   coend;
   {
   Fin de la seccion para los procesos de forma concurrente.
   }
   writeln('Solucion:');
   mostrarMatriz;
 end.
