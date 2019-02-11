def cargar_archivo(lab):
    return open(lab)


## Mat es la copia de la matriz que se carga en el archivo,fil (fila inicial), col (Columna inicial) , aux ( Ayuda a controlar el tamaño de la matriz
## para no salirse del limite), tam (es el tamaño del lado de la matriz cargada nxn)

def Derecha(mat,fil,col,aux,tam):

    
    if(tam>0):
        # Si el tamaño de aux no supera el tamaño de la matriz, imprime las coordenadas iniciales que se le dieron y luego se suma 1 a la columna para
        # avanzar por columna hacia la derecha.
        if(aux<tam):
            print(mat[fil][col])
            # Recursividad
            Derecha(mat,fil,col+1,aux+1,tam)

        # cuando el tamaño auxiliar es igual al tamaño de lado n de la matiz quiere decir que se paso 1 columna fuera de la matriz
        # por lo tanto se resta 1 columna y se agrega 1 fila para continuar con el siguiente dato y se resta 1 en el tamaño de la matriz
        # para imprimir los otros datos sin pasar del limite. (La nueva fila y columna pasa a la funcion de mvoer abajo)
        if(aux==tam):
            Abajo(mat,fil+1,col-1,0,tam-1)
    else:
        print("")

def Abajo(mat,fil,col,aux,tam):
    if(tam>0):
        if(aux<tam):
            print(mat[fil][col])
            Abajo(mat,fil+1,col,aux+1,tam)
        if(aux==tam):
            Izquierda(mat,fil-1,col-1,0,tam)
    else:
        print("")
def Izquierda(mat,fil,col,aux,tam):
    if(tam>0):
        if(aux<tam):
            print(mat[fil][col])
            Izquierda(mat,fil,col-1,aux+1,tam)
        if(aux==tam):
            Arriba(mat,fil-1,col+1,0,tam-1)
    else:
        print("")
        
def Arriba(mat,fil,col,aux,tam):
    if(tam>0):
        if(aux<tam):
            print(mat[fil][col])
            Arriba(mat,fil-1,col,aux+1,tam)
        if(aux==tam):
            Derecha(mat,fil+1,col+1,0,tam)
    else:
        print("")

# Funcion a la que se envia una matriz vacia y la matriz que viene del archivo para ser cargada
def crear_mat(mat,lab):
    for x in cargar_archivo(lab):
        mat.append(x.strip().split())
        # Retorna la matriz ya llena con los datos cargados
    return mat

    
# funcion a la que se envian los datos de entrada suponiendo que se comienzan desde las coordenadas 0,0 y hacia la derecha

def RecorrerMatriz(lab):
    Derecha(crear_mat([],lab),0,0,0,len(crear_mat([],lab)))
    
          
RecorrerMatriz("Matriz.txt")
