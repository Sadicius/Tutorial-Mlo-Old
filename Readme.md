# Resumen

1.CODEWALKER
    - EXTERIOR + DETAIL + Texture
    - COLLISION + DETAIL
    - EMMISSIVE
    - OCCLUSION
    - YMAP
    - ESTRUCTURA DE PEDIDO

2.BLENDER
    - EXTERIOR UND COLLISION ZUSAMMEN POSITIONIEREN
    - EXTERUIR, COLLISION BEARBEITEN
    - CERANDERTE POSITIONEN ZURUCKSETZEN UND EXPORTIEREN
    - MLO + MLO_COLLISION PASSIG ZUM EXTERIOR MACHEN
    - MLO DEFAULT SHADER + EMBEDDED + WENIG FISCHEN UND PUNKTE
    - MLO COLLISION + MATERIAL + ROOMID + FLAGS
    - YTYP ERSTELLEN (ROOMID, LIMBO FLAG 96, Bmin + Bmax PASSIG)
    - NORMALS UBERPRUFEN
    - DATEN EXPERTIEREN

3.RPF
    - DLC ERSTELLEN
    - IMPORT UND KONTROLLE
    - CUSTOM DLC FOR SERVER

4.CODEWALKER
    - YMAP + MANIFEST

5.SERVERTEST



# README
## PASOS A SEGUIR PARA LA REALIZACIÓN DE UN MLO

--------------------------------------------------------------------------------------------------------------------------------------------

CODEWALKER
    1. EXTERIOR + DETAIL + Texture
        Localizar edificio para modelar, mediante CODEWALKER
            Ejemplo:    'cs1_03_shps1_dets'   >   localizacion mediante los detalles de un edificio

        Abrir el Tools > RPF Explorer
            Ejemplo:    'cs1_03_shps1'        >   localizacion de archivos .ydr

        Buscar por referencia del nombre del archivo o modelo 
            Archivos:   'cs1_03_shps1+hidr.ytd'       Type: Texture   Atributes:  V.13    Path: mods
                        'cs1_03_shps1.ydr'            Type: Drawable  Atributes:  V.165   Path: mods
                        'cs1_03_shps1_dets.ydr'       Type: Drawable  Atributes:  V.165   Path: mods
                        'cs1_03_shps1+hidr.ytd'       Type: Texture   Atributes:  V.13    Path: update
                        'cs1_03_shps1.ydr'            Type: Drawable  Atributes:  V.165   Path: update
                        'cs1_03_shps1+hidr.ytd'       Type: Texture   Atributes:  V.13    Path: update
                        'cs1_03_shps1.ydr'            Type: Drawable  Atributes:  V.165   Path: update
                        'cs1_03_shps1+hidr.ytd'       Type: Texture   Atributes:  V.13    Path: x64g
                        'cs1_03_shps1.ydr'            Type: Drawable  Atributes:  V.165   Path: x64g      > seleccionar este       
                        'cs1_03_shps1_dets.ydr'       Type: Drawable  Atributes:  V.165   Path: x64g

        Revisar en View los apartados siguientes
            Mode: World view
            Max LOD: ORPHANHD
            Detail distance: 1.0
            Show scripted ymaps             > Check
            Filter ympas by time of day     > Check
            Filter ympas by weater          > Check
            Enable Mods                     > Check
            Enalbe DLC                      > Check
            DLC Level: mpsecurity
        
        Exportar archivo seleccionado .ydr (Type: Drawable) en formato XML
            Ejemplo:    'cs1_03_shps1.ydr'
        Exportar texturas
            Abrir View (Ctrl + P)
            Abrir desplegable '>>' + Seleccionar 'Materials' 
            Guardar texturas 'Save all textures' dentro de carpeta de materiales 'cs1_03_shps1'

    2. COLLISION + DETAIL
        Localizar colisiones edificio para modelar, mediante CODEWALKER
        Cambiar Mode 'Collision'
        Seleccionar colisiones 
            Ejemplo:    Poly 420: 'cs1_03_0.ybn'

        Abrir el Tools > RPF Explorer
            Ejemplo:    'cs1_03_shps1.ybn'        >   localizacion de archivos .ybn
        
        Buscar por referencia del nombre del archivo o modelo 
            Archivos:   'cs1_03_0.ybn'              Atributes:  V.43   Path: mods
                        'hi@cs1_03_0.ybn'           Atributes:  V.43   Path: mods
                        'ma@cs1_03_0.ybn'           Atributes:  V.43   Path: mods
                        'cs1_03_0.ybn'              Atributes:  V.43   Path: x64g       > Seleccionar este
                        'hi@cs1_03_0.ybn'           Atributes:  V.43   Path: x64g
                        'ma@cs1_03_0.ybn'           Atributes:  V.43   Path: x64g
        
        Revisar en View, Exportar archivo seleccionado .ybn en formato XML
            Ejemplo:    'cs1_03_0.ybn'
        Revisar otras versiones: cs1_03_0.ybn > cs1_03_1.ybn > cs1_03_2.ybn Exportar archivo seleccionado .ybn en formato XML
            Ejemplo:    'hi@cs1_03_2.ybn'

    3. EMMISSIVE
        Localizar luces y texturas de noche en edificio para modelar, mediante CODEWALKER
        Cambiar Mode 'Entity'
        Cambiar la hora del Dia, ver cambios de texturas 'on' / 'off' 
            Ejemplo:    'cs1_03_emissive_12'
        Exportar archivo seleccionado si es necesario   > ¿?

    4. OCCLUSION (minuto 8:15)
        Primera parte > Localizar oclusiones edificio para modelar, mediante CODEWALKER
        Cambiar Mode 'Occlusion'
        Seleccionar oclusiones 
            Ejemplo:    'BoxOccluder cs1_occl_10ymap 82'
            Ymap:       'cs1_occl_10.ymap'

        Abrir el Tools > RPF Explorer
            Ejemplo:    'cs1_occl_10.ymap'        >   localizacion de archivos .ymap

        Buscar por referencia del nombre del archivo o modelo 
            Archivos:   'cs1_occl_10.ymap'              Atributes:  V.2   Path: mods
            Archivos:   'cs1_occl_10.ymap'              Atributes:  V.2   Path: x64g    > Seleccionar este

        Exportar archivo seleccionado .ymap (Type: Map Data) en formato XML
            Ejemplo:    'cs1_occl_10.ymap'

        Seguimos en modo 'Occlusion'
        Segunda parte > Bloques Azules
            Buscar la información que aparece en la pestaña de 'BoxOccluder' en Box > iCenterX
                Ejemplo:    'iCenterX: -66'
            Revisar ymap.XML > Abrir en VisualCode
                Ejemplo:    'cs1_occl_10.ymap.xml'
            Buscar la coordenada iCenterX 
                Ejemplo:    <Item>
                            <iCenterX value="-66" />
                            <iCenterY value="25946" />
                            <iCenterZ value="117" />
                            ... seguir hasta el siguiente <Item />
            Eliminar seccion complenta de <Item> a <Item/> 

            Repetir el proceso por si existen mas BoxOccluder que afecten al modelo
            Buscar, seleccionar, comprobar iCenterX y eliminar seccion
                Ejemplo:    <Item>
                            <iCenterX value="-68" />
                            <iCenterY value="25944" />
                            <iCenterZ value="113" />
                            ... seguir hasta el siguiente <Item />

            Repetir el proceso por si existen mas BoxOccluder que afecten al modelo edificios colindantes
            Buscar, seleccionar, comprobar iCenterX y eliminar seccion
                Ejemplo:    <Item>
                            <iCenterX value="-31" />
                            <iCenterY value="25980" />
                            <iCenterZ value="111" />
                            ... seguir hasta el siguiente <Item />

            Cerrar archivo de VisualCode

        Tercera parte > Bloques Rojos
        Buscar la información que aparece en la pestaña de 'Occlude Trianle' en Model > Occludel 
            bmin            (x, y, z)
            bmax            (x, y, z)
            numVertsBytes   '2496'
            numTips         '33059'
            
    5. YMAP
        Localizar ymap edificio para modelar, mediante CODEWALKER
        Cambiar Mode 'Entity'
        Seleccionar Entity > Ymap 
            Ejemplo:    'hei_cs1_03_strm_1.ymap'

        Abrir el Tools > RPF Explorer
            Ejemplo:    'hei_cs1_03_strm_1.ymap'        >   localizacion de archivos .ymap

        Exportar archivo seleccionado .ymap (Type: Map Data) en formato XML
            Ejemplo:    'hei_cs1_03_strm_1.ymap'

    6. ESTRUCTURA DE PEDIDO
        Resumen (archivos descargados para la preparacion de la base para el MLO) 
            'cs1_03_shps1_dets.ydr.xml'     > Drawable
            'cs1_03_shps1'                  > Carpeta con las texturas
            'cs1_03_shps1.ydr.xml'          > Drawable
            'cs1_03_0.ybn.xml'              > Colisiones
            'hi@cs1_03_2.ybn.xml'           > Colisiones
            'cs1_occl_10.ymap.xml'          > Occlusiones ymap
            'hei_cs1_03_strm_1.ymap.xml'    > ymap

        Crear Carpetas
            'Test'
            'map-Test'
            'dlc-Test'

        Copiar Base de 'map-tutorial' > Pegar en carpeta 'map-Test'
        Archivos:
            'stream'      > Carpeta para los archivos
            'resource.cfg'
            'stream.cfg'

        Revisar carpeta stream > assets
            Seleccionar todos los archivos y eliminarlos
        
        Mover a la carpeta 'Test'
        'cs1_occl_10.ymap.xml'          > Occlusiones ymap

        Crear carpeta Test > Original y pegar el resto de archivos
        'cs1_03_shps1_dets.ydr.xml'     > Drawable
        'cs1_03_shps1'                  > Carpeta con las texturas
        'cs1_03_shps1.ydr.xml'          > Drawable
        'cs1_03_0.ybn.xml'              > Colisiones
        'hi@cs1_03_2.ybn.xml'           > Colisiones
        'hei_cs1_03_strm_1.ymap.xml'    > ymap

        Repetir ultimo paso pero en la carpeta 'Test'

----------------------------------------------------------------------------------------------
Ref https://www.youtube.com/watch?v=aq-k2sAxS6M
Min hasta la ultima linea 14:37
----------------------------------------------------------------------------------------------

BLENDER
    PREVIOS 
        Preparacion de coleciones Blender 
            EXTERIOR
            EXTERIOR_2
            EXTERIOR_COLLUSION
            EXTERIOR_COLLUSION_2
            INTERIOR
            INTERIOR_COLLUSION 
        Guardar archivo test.blend
        
    EXTERIOR DE POSICIÓN Y COLISIÓN JUNTOS
        Previo
            Abrir el Sollumz > General Tools > Ymap Tools 
            Importar archivos .xml      > EXTERIOR
                cs1_03_shps1.ydr.xml 
                    BatchModus:
                    Animation: 
                    Skellet > Import External Skeleton > OFF 
                    Fragment > Split > OFF 
                    Geometrie > Join Geometries > OFF
                cs1_03_shps1_dets.ydr.xml  
                cs1_03_0.ybn.xml
                hi@cs1_03_2.ybn.xml

            Abrir Viewport Overlays > Desactivar opcion Extras y debajo de Extras 
            Abrir desplegable Shading > Activar texturas
        Parte 1
            Seleccionar 'cs1_03_0' > Ir al menu de Sollumz > Collision Tools  
            Pulsar en 'Center Composite'
            Ir seleccionando el resto de archivos y revisar si posibilidad de Pulsar en 'Center Composite'
            Seleccionar 'hi@cs1_03_2' > Ir al menu de Sollumz > Collision Tools  
            Pulsar en 'Center Composite'
        Parte 2
            Seleccionar 'cs1_03_0' > Ir al menu de Sollumz > General Tools > Ymap > Impor ymap.xml
                Archivo:    hei_cs1_03_strm_1.ymap.xml
            Seleccionar todo y copiar o mover 'cs1_03_0' a la colleccion 'EXTERIOR_COLLUSION'
        Parte 3
            Seleccionar 'cs1_03_shps1_dets' > Ir al menu de Sollumz > General Tools > Ymap > Impor ymap.xml
            Seleccionar todo y copiar o mover 'cs1_03_shps1_dets' a la colleccion 'EXTERIOR_2'
        Parte 4
            Seleccionar 'hi@cs1_03_2' > Ir al menu de Sollumz > General Tools > Ymap > Impor ymap.xml
            Seleccionar todo y copiar o mover 'hi@cs1_03_2' a la colleccion 'EXTERIOR_COLLUSION_2'
    
    EXTERIOR, EDITAR COLISIÓN
        Apagar todas las colleciones menos EXTERIOR 
        Seleccionar puerta > Pulsar Archivo > Tercera opcion 
        Abrir modo Edición > Seleccionar plano > seleccionar punto y borde
            Seleccion de todos triangulos de huecos
            Eliminar superficies seleccionadas
        Seleccionar todo (boton derecho raton)

        Revisar configuración para Exportar archivo exteior modificado
        Abrir pestaña de Sollumz > General Tools > Export Code
            Revisar     Limit to    Opcion 1 > ON 
                                    Opcion 2 > OFF 
                        Sollum Types    Drawables  > ON
                                        Drawables Dictionarys > ON
                                        Begrenzung > ON
                                        Fragments  > ON
                                        Clip Dictionary > ON 
                                    Export with YTYP > OFF 
                        Fragment    Export With_hi >OFF 
                        Ausschi     Skellet > OFF 
                        Batch-Modus AUS 
                        Geometrie   Use Parent transfor.. > OFF
            Finalizar pulsando export
        
        Abrir vision colleccion EXTERIOR_2
            Revisar la existencia de caras y eliminarlos
            Seleccionar todo (boton derecho raton)
            Revisar configuración para exportar
            Finalizar pulsando export

        Abrir vision colleccion EXTERIOR_COLLUSION
            Verificar que caso es A o B
                Opcion A - Revisar la existencia de caras y eliminarlos 
                Opcion B - Revisar y crear hueco 
                    Seleccionar cara > Ir a la sección de Sollumz > Collision Tools > Create Bounds
                    Seccion 'Create Poly' > Seleccionar Tipo 'Bound Poly Mesh'
                    Revisar configuración
                        Use > ON 
                        Orig > ON
                        Cen > ON
                        Sep > OFF
                        BVH > ON
                    Abrir hueco
            Seleccionar todo (boton derecho raton)
            Revisar configuración para exportar
            Finalizar pulsando export

        Abrir vision colleccion EXTERIOR_COLLUSION_2
            Apagar vision de EXTERIOR_COLLUSION para ver mejor el hueco 
            Verificar que caso es A o B
                Opcion A - Revisar la existencia de caras y eliminarlos 
                Opcion B - Revisar y crear hueco 
            Apagar visión de EXTERIOR y activar EXTERIOR_COLLUSION
            Seleccionar todo (boton derecho raton)
            Revisar configuración para exportar
            Finalizar pulsando export
            
    RESTABLECER Y EXPORTAR PUESTOS MODIFICADOS
        Resumen se han exportado las modificaciones con los siguientes archivos
            'cs1_03_shps1_dets.ydr.xml'     > Drawable  modificado
            'cs1_03_shps1.ydr.xml'          > Drawable  modificado
            'cs1_03_0.ybn.xml'              > Colisiones  modificado
            'hi@cs1_03_2.ybn.xml'           > Colisiones modificado

    MLO + MLO_COLLISION HACER PASAR AL EXTERIOR
        Activar vision de la colleccion 'cs1_03_shps1' > EXTERIOR 
        Seleccionar la vision collecion 'INTERIOR'
        --> Se puede empezar a modelar
        Crear Cubo
        Desplazar modelo EXTERIOR a coordenadas (0,0,0)
        MODELAR ESPACIOS --> Disño a tu gusto
        Apagar vision de EXTERIOR solo dejar la vision INTERIOR

        Una vez terminado el modelo o diseño, es necesario LIMPIAR 
            Seleccionar todo Malla > Fusionar > Por distancia 
            Unir o limpiar caras del modelo 
            Guardar archivo (Minuto 35:53)

        Abrir desplable, activar lados de caras en Geometrie (Vision Azul y Rojo)
        Invertir caras, Azul Interior / Rojo Exterior 
        Activar vision colleccion EXTERIOR e INTERIOR y revisar union 
            Una vez revisados continuar con solo INTERIOR
        
        Abrir propiedades > Transformación
        Abrir Sollumz > Drawable Tools > Create Drawable Objects
            Revisar configuración 
                Type: Drawable 
                Use > ON 
                Center > ON 
                Separate > OFF 
                Auto > OFF
            Seleccionar el modelo Interior
            Pulsar en 'Create Drawable'
        Comprobar los Sollumz Types 

        Copiar Modelo INTERIOR y pegarlo en INTERIOR_COLLUSION
        Apagar visión colleccion INTERIOR 
        Seleccionar collección INTERIOR_COLLUSION 
        Abrir Sollumz > Collision Tools > Create Bounds 
            Revisar configuración 
                Type Bount Composite
                    Use > ON 
                    Original > ON
                    Center > ON 
                    Separate > OFF 
                    BHV > ON
                Pulsar en 'Create Bound'
        
        Revisar estructura, estado original 
            INTERIOR_COLLUSION
                Bound Composite --> Simbolo de lazo 
                    Bound GeometryBHV  --> Simbolo de lazo
                Modelo  --> Simbolo de lazo
                    Drawable Model  --> Simbolo de lazo
                        Modelo_dibujo --> Simbolo de triangulo

        Estado final estructura, estado modificado 
            INTERIOR_COLLUSION
                Bound Composite --> Simbolo de lazo 
                    Bound GeometryBHV  --> Simbolo de lazo
                    Modelo_dibujo --> Simbolo de triangulo
                Modelo  --> Simbolo de lazo
                    Drawable Model  --> Simbolo de lazo

        Abrir Sollumz > Collision Tools > Create Bounds 
        Revisar configuración 
            Type Bount Poly Mesh
                Use > ON 
                Original > ON
                Center > ON 
                Separate > OFF 
                BHV > ON
            Pulsar en 'Create Bound Poly'

        Eliminar partes de INTERIOR_COLLUSION no necesarias
            Modelo  --> Simbolo de lazo
            Drawable Model  --> Simbolo de lazo
        
        Abrir Sollumz > Collision Tools > Flags 
            Deberia existir una ya --> Vorgabe
        Abrir Propiedades > Casilla de Transformación > Sollumz > Collision Flags 
            Aplicar Flag 'Vorgabe'
            Revisar configuración  
            Composite flags 1 
                MAP > ON
                MAP D > ON 
                MAP A > ON 
                MAP C > ON 
                MAP V > ON 
            Composite flags 2
                UNKN      > ON      PED      > ON   EXPLO      > ON     TEST     > ON
                MAP       > ON      RAGD     > ON   PICKUP     > ON     GLASS    > ON
                MAP D     > ON      ANIMAL   > ON   FOLIA      > ON     MAP R    > ON
                MAP A     > ON      ANIM     > ON   FORK       > ON     SMOKE    > ON
                MAP C     > ON      OBJECT   > ON   TEST       > ON     UNSM     > ON
                MAP V     > ON      OBJEC    > ON   TEST       > ON     MAP S    > ON
                VEHIC     > ON      PLANT    > ON   TEST AI    > ON     MAP D    > ON
                VEHIC     > ON      PROJE    > ON   TEST S     > ON

        Cambiar el nombre para no generar conflicto INTERIOR
        Cambiar el nombre para no generar conflicto INTERIOR_COLLUSION

        Apagar vision de INTERIOR_COLLUSION solo dejar la vision INTERIOR

    MLO DEFAULT SHADER + INTEGRADO + PEQUEÑA PESCA Y PUNTOS
    Parte 1
        Seleccionar todo
        Ir a la seccion Sharing 
        Abrir propiedades > Materiales 
        Abrir Sollumz > Drawable Tools > Create Shader > Default 
        Pulsar 'Create Shader Material'
            Se crea Material default.001 > Seleccionarlo y cambiar el nombre 
        Dentro de las propiedades de material > Sollumz 
            Desplegar   Value Parameters 
                        Texture Parameters > Activar Embedded 
        Ir al cuadro de conexiones Sharing > En el cuadro de 'Texture' > Seleccionar Abrir carpeta > Seleccionar 'Archivo textura' 
            Con esto generamos todas las texturas necesarias una por una solo con crear un default, cambiarle el nombre, cambiar la imagen 
    Parte 2
        Ir a la seccion UV Edding 
        Seleccionar cara 
        Menu UV > Pulsar en el apartado 5
        Cambiar vision a textura
        Ajustar textura > Escalando en la zona 2d
----------------------------------------------------------------------------------------------
Ref https://www.youtube.com/watch?v=aq-k2sAxS6M
Min hasta la ultima linea 45:00
----------------------------------------------------------------------------------------------
    Parte 3 
        Seleccionar todo    
        Exportar Sollumz > General Tools > Export Code 

    COLISIÓN MLO + MATERIAL + ROOMID + BANDERAS (FLAG)
    Parte 1
    Seleccionar todo 
        Collision Tools > Create Collision Material > Seleccionar en buscador el material a elegir 'CERAMIC'  
        Pulsar 'Create Collision Material' con la superficie o cara seleccionada 
        Cambiar nombre de material para poner el mismo que el usado antes  'default_col'
        Una vez creado el material en Collision > Ir a propiedades de material > Sollumz
            Con el materia de la cara seleccionada cambiar 'RoomID' 0 por 1  solo en el Suelo
    Una vez terminado exportar INTERIOR_COLLUSION a xml

    Parte 2 
    Selecciona todo Interior 
    Ir a Sollumz > General Tools > Vertex Palnter 
        Seleccionar el color y cambiarlo a gusto 
        Pulsar en 'Paint'
        Comprobar el estado cambiando el estilo de vista a Atributo
    Una vez terminado exportar INTERIOR a xml

----------------------------------------------------------------------------------------------
Ref https://www.youtube.com/watch?v=aq-k2sAxS6M
Min hasta la ultima linea 52:26
----------------------------------------------------------------------------------------------

    CREAR YTYPE (ROOMID, LIMBO FLAG 96, Bmin + Bmax PASSIG)
    Parte 1 
        Activar vision de collecion INTERIOR 
        Ir a Sollumz > Archetype Definition > YTYPS
            Pulsar 'Create YTYP'
        Abrir desplegable YTYP.1 > Cambiar el nombre mlo1 
        Seleccionar modelo INTERIOR 
            Revisar configuración 'Auto-Create F'
                Type: Basis
            Pulsar 'Auto-Create F'
        Se crea un mlo1 en Archetypes 
    Parte 2
        Activar vision de collecion INTERIOR_COLLUSION 
        Ir a Sollumz > Archetype Definition > YTYPS
            Pulsar 'Create YTYP'
        Abrir desplegable YTYP.1 > Cambiar el nombre mlo1_collision 
        Seleccionar modelo INTERIOR 
            Revisar configuración 'Auto-Create F'
                Type: MLO
            Pulsar 'Auto-Create F'
        Se crea un mlo1 en Archetypes 
    Parte 3
        Abrir desplegable Archetype 
            Seleccionar 'mlo1'
            Ir a la Seccion de Physics Dictionary > Introducir texto 'mlo1' 
    Parte 4
        En el desplegable Archetype 
            Seleccionar 'mlo1_collision'
            Ir a la Seccion de Rooms > Pulsar en 'Create Limbo Room'
            Se crea una habitación como 0:limbo 
            Revisa > Marcar en 'Show Room Gizmo'
            Vuelve a Pulsar en 'Create Limbo Room'
            Cambia el Name 'raum1'
    Parte 5 
        Desplegar Flaggen > 
        Revisar Flaggen : 32 
        Marcar Reduces vehicle popul 
        Marcar Reduces ped population
        Cofirmar aumento revisar Flaggen : 96 
    Parte 6 
        Desplegar Entities  >  Seleccionar INTERIOR 
        Pulsar 'Add Selected Object(s) as Entity' > Se crea un 'mlo1' en Entities  
        Revisar LOD Level 'DEPTH ORPHAN HD'
        Revisar Priority Level 'REQUIRED'
        Modificar Lod Distance de 200 a 500
        Revisar en Attached Room > Pulsar 'Set to Selecction' > seleccionar limbo
    Parte 7 
        Desplegar Portals
        Marcar 'Show Portal Gizmo'
        Seleccionar todo y abrir la seccion de modelado
        Seleccionar los vertices de los portales > Pulsar 'Create Portal From Verts' 
        Se crea un portal > marcar en Room From > Pulsar en 'Set to Selected' para cambiar de 'limbo' a 'raum1'
        Repetir proceso con los demas ESPACIOS
    Parte 8
        Desplegar Flaggen > 
        Marcar Hide When door closed > ON 
        Marcar Disable farclipping > ON

--[[         Marcar Disables exterior render > ON 
        Marcar Extra bloom > ON  ]]

    Parte 9
        Ir arriba a la seccion principal de YTYP 
        Pulsar Export ytyp.xml > Guardar en la carpeta TEST > Se crea un archivo 'mlo1.ytyp.xml'

----------------------------------------------------------------------------------------------
Ref https://www.youtube.com/watch?v=aq-k2sAxS6M
Min hasta la ultima linea 58:10
----------------------------------------------------------------------------------------------

    COMPROBAR NORMALMENTE
        Abrir Codewalker > Tools > RPF EXPLORER
        Ir a ruta GTAV/MODS/UPDATE.RPF/X64/DLCPACK/CUSTOM_DLC/DLC.RPF/X64/LEVELS/GTA5
        Copiar dentro de la ruta la carpeta 'DLC_TEST' 
        Desde la carpeta 'TEST' > Copiar los 12 archivos y arrastrarlos a la carpeta DLC_TEST dentro de la ruta
            Archivos 
            'cs1_03_shps1_dets.ydr.xml'     
            'cs1_03_shps1'                  
            'cs1_03_shps1.ydr.xml'          
            'cs1_03_0.ybn.xml'              
            'hi@cs1_03_2.ybn.xml'           
            'hei_cs1_03_strm_1.ymap.xml'   
            'mlo1.ydr.xml'
            'mlo1.ytyp'
            'mlo1_collision.ybn.xml' 

    DATOS EXPERTOS
        Con los archivos dentro del codewalker > Seleccionar uno a uno y revisarlo con View 
        Una vez comprobado cada uno arrastrar el archivo del codewalker a la carpeta 'MAPS-TEST'
        'cs1_03_shps1_dets.ydr'     
        'cs1_03_shps1'                  
        'cs1_03_shps1.ydr'          
        'cs1_03_0.ybn'              
        'hi@cs1_03_2.ybn'   
        'mlo1.ydr'
        'mlo1.ytyp'
        'mlo1_collision.ybn' 
        Eliminar 'hei_cs1_03_strm_1.ymap' 

# RPF
    CREAR DLC
        Selection > Mouse > ON 
        Nuevo > YMAP file
        Se abre New Codewalker Project  
            Name : Poner nombre 'mlo1'
            Pulsar 'Calculate all flags'
            Pulsar 'Calculate extents'

    IMPORTACIÓN Y CONTROL
        Ymap > Entity 
            Archetype : Poner nombre 'mlo1' > Comprobar el HASH 
            Cambiar el nombre a 'mlo1_collision' 
            Pulsar 'Calculate all flags'
            Pulsar de nuevo 'Calculate extents'
        En el Codewalker desplazar los modelos hasta localizar el que interesa
            Una vesz localizado > Buscar la Positión (x,y,z) y la copiamos 
            Eliminar del proyecto la referencia de la busqueda mediante Ymap > Remove from Project
            Eliminar el ymap resultante


    DLC PERSONALIZADO PARA SERVIDOR
        Vuelve a la pestaña del proyecto mlo1.ymap 
        Ymap Files > mlo1.ymap > Entities > Seleccionar mlo1_collision 
            Pegar las coordenadas conseguidas antes
        Pulsar 'Calculate all flags'
        Pulsar de nuevo 'Calculate extents'

        Guardar File > mlo1.ymap As
            Seleccionar carpeta de TEST 
            Una vez guardado, cerrar la ventana File > Closing Project sin guardar

CODEWALKER
    YMAP + MANIFIESTO
        Volver a abrir el proyecto > Revisar 
        Una vez revisado Tools > Manifest Generator
            Pulsar 'Generate'
            Pulsar en 'Save _manifest.ymf'
            Cambiar el nombre _manifest.ymf por '_manifest_test.ymf'
        
        Una vez terminado, ir a la carpeta TEST 
        copiar el archivo '_manifest_test.ymf' a la carpeta MAPS-TEST
        copiar el archivo 'mlo1.ymap' a la carpeta MAPS-TEST

        Revisión de archivos dentro de la carpeta MAPS TEST > stream > assets 
        'cs1_03_shps1_dets.ydr'     
        'cs1_03_shps1'                  
        'cs1_03_shps1.ydr'          
        'cs1_03_0.ybn'              
        'hi@cs1_03_2.ybn'   
        'mlo1.ydr'
        'mlo1.ytyp'
        'mlo1_collision.ybn'
        'mlo1.ymap'
        'mlo1.ytyp'
        '_manifest_test.ymf'

PRUEBA DEL SERVIDOR
    Añadir carpeta al servidor y activar el mapa 
    ensure mlo1
