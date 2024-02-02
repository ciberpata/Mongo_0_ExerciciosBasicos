# Exercicios
## Base de datos libros

> Crea unha función en JS para insertar a través desa función a seguinte bbdd
load
Respuesta: es el fichero /ExamenDia27/libros.js
use libros

Cambiar a la carpeta /ExamenDia27

load("libros.js")




```js
db.libros.insertOne(
  {
    _id: 1,  
    titulo: 'El aleph',
    autor: 'Borges',
    editorial: ['Siglo XXI','Planeta'],
    precio: 20,
    cantidade: 50 
  }
)
db.libros.insertOne(
  {
    _id: 2,  
    titulo: 'Martin Fierro',
    autor: 'Jose Hernandez',
    editorial: ['Siglo XXI'],
    precio: 50,
    cantidade: 12
  }
)
db.libros.insertOne(
  {
    _id: 3,  
    titulo: 'Aprenda PHP',
    autor: 'Mario Molina',
    editorial: ['Siglo XXI','Planeta'],
    precio: 50,
    cantidade: 20
  }
)
db.libros.insertOne(
  {
    _id: 4,  
    titulo: 'Java en 10 minutos',
    editorial: ['Siglo XXI'],
    precio: 45,
    cantidade: 1 
  }
)
```


- Insertar 2 documentos na colección libros
db.libros.insertOne({_id: "mio_1", titulo:"Mi primer registro"})
db.libros.insertOne({_id: "mio_2", titulo:"Mi segundo registro"})

- Intentar insertar un documento con clave repetida (qué di a consola?, o permite?)
MongoServerError: E11000 duplicate key error collection: libros.libros index: _id_ dup key: { _id: "mio_2" }

- Mostrar todos os documentos
db.libros.find()

- Agrega unha colección chamada "posts" e inserta 1 documento cunha estructura calquera
use posts
db.posts.insertOne({_id: 1, 'nombre Programa': 'Dreamweaver'})

- Cantas bbdd podes visualizar agora mesmo?
show dbs que devuelve 7 bbdd.

- Elimina a coleción chamada "posts"
db.dropDatabase()
{ ok: 1, dropped: 'posts' }

- Crea outra bbdd chamada borrar, introdúcelle un dato calquera
 db.createCollection('borrar')
{ ok: 1 }

db.borrar.insertOne({_id: 'OtroRegistro', programa: 'Visual Studio Code'})
{ acknowledged: true, insertedId: 'OtroRegistro' }

- Borra a base de datos creada no punto anterior.
db.dropDatabase()
{ ok: 1, dropped: 'posts' }

## Base de datos artigos
- Crea a seguinte bbdd, elixe un nome apropiado:
use artigos
switched to db artigos

load("artigos.js")
true

```js
db.artigos.insertOne(
  {
    _id: 1,  
    nome: 'MULTIFUNCION HP DESKJET 2675',
    rubro: 'impresora',
    precio: 3000,
    stock: 20 
  }
)
db.artigos.insertOne(
  {
    _id: 2,  
    nome: 'MULTIFUNCION EPSON EXPRESSION XP241',
    rubro: 'impresora',
    precio: 3700,
    stock: 5 
  }
)
db.artigos.insertOne(
  {
    _id: 3,  
    nome: 'LED 19 PHILIPS',
    rubro: 'monitor',
    precio: 4500,
    stock: 2
  }
)
db.artigos.insertOne(
  {
    _id: 4,  
    nome: 'LED 22 PHILIPS',
    rubro: 'monitor',
    precio: 5700,
    stock: 4
  }
)
db.artigos.insertOne(
  {
    _id: 5,  
    nome: 'LED 27 PHILIPS',
    rubro: 'monitor',
    precio: 12000,
    stock: 1
  }
)

db.artigos.insertOne(
  {
    _id: 6,  
    nome: 'LOGITECH M90',
    rubro: 'mouse',
    precio: 300,
    stock: 4
  }
)


```
### Utilización de comparadores
- Imprime todos os datos da bbdd creada
db.artigos.find()

- Imprimir todos os artigos que pertencen ou rubro de 'mouse'.
db.artigos.find({rubro:'mouse'})
[  
  {
    _id: 6,
    nome: 'LOGITECH M90',
    rubro: 'mouse',
    precio: 300,
    stock: 4
  }
]

- Imprimir todos os artigos cun precio maior o igual a 5000.
 db.artigos.find({precio:{$gte:5000}})
[  
  {
    _id: 4,
    nome: 'LED 22 PHILIPS',
    rubro: 'monitor',
    precio: 5700,
    stock: 4
  },
  {
    _id: 5,
    nome: 'LED 27 PHILIPS',
    rubro: 'monitor',
    precio: 12000,
    stock: 1
  }
]

- Imprimir todas as impresoras que teñen un precio maior ou igual a 3500.
db.artigos.find({rubro:'impresora', precio:{$gte:3500}})
[  
  {
    _id: 2,
    nome: 'MULTIFUNCION EPSON EXPRESSION XP241',
    rubro: 'impresora',
    precio: 3700,
    stock: 5
  }
]

- Imprimir todos os artigos cuxo stock atópase comprendido entre 0 y 4.
db.artigos.find({ stock: { $gte: 0, $lte: 4 } })
[  
  {
    _id: 3,
    nome: 'LED 19 PHILIPS',
    rubro: 'monitor',
    precio: 4500,
    stock: 2
  },
  {
    _id: 4,
    nome: 'LED 22 PHILIPS',
    rubro: 'monitor',
    precio: 5700,
    stock: 4
  },
  {
    _id: 5,
    nome: 'LED 27 PHILIPS',
    rubro: 'monitor',
    precio: 12000,
    stock: 1
  },
  {
    _id: 6,
    nome: 'LOGITECH M90',
    rubro: 'mouse',
    precio: 300,
    stock: 4
  }
]

- Imprimir todos os documentos da colección 'artigos' que non son impresoras.
db.artigos.find({rubro:{$ne:'impresora'}})
[  
  {
    _id: 3,
    nome: 'LED 19 PHILIPS',
    rubro: 'monitor',
    precio: 4500,
    stock: 2
  },
  {
    _id: 4,
    nome: 'LED 22 PHILIPS',
    rubro: 'monitor',
    precio: 5700,
    stock: 4
  },
  {
    _id: 5,
    nome: 'LED 27 PHILIPS',
    rubro: 'monitor',
    precio: 12000,
    stock: 1
  },
  {
    _id: 6,
    nome: 'LOGITECH M90',
    rubro: 'mouse',
    precio: 300,
    stock: 4
  }
]

### Borrado de datos
> Lembra que as funcións son <span style="color:yellow;">deleteOne</span> e <span style="color:yellow;">deleteMany</span>
- Borra os documentos da colección 'artigos' onde 'rubro' son 'impresoras'
 db.artigos.deleteMany( {rubro: 'impresora' } )
{ acknowledged: true, deletedCount: 2 }

- Borra todos os artigos que teñen un '_id' maior ou igual a 5.
 db.artigos.deleteMany( {_id: {$gte:5} } )
{ acknowledged: true, deletedCount: 2 }

### Modificación 
> Lembra que as funcións son <span style="color:yellow;">updateOne</span> e <span style="color:yellow;">updateMany</span>
- Borra a base de datos creada de artigos.
db.artigos.drop()
true

- Volver crear a base de datos de artigos de novo.
use artigos
switched to db artigos

load('artigos.js')
true

- Modifica o prezo do mouse 'LOGITECH M90'
db.artigos.updateOne({nome:'LOGITECH M90' }, {$set: {precio: 1234568}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

- Fixa o stock en 0 do artigo onde o '_id' é 6.
 db.artigos.updateMany({_id:6 }, {$set: {stock: 0}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
- Fixa o stock de todos os artigos a 0.
db.artigos.updateMany({}, {$set: {stock: 0}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 6,
  modifiedCount: 5,
  upsertedCount: 0
}

- Modifica o artigo con '_id' = 6, o cal deberá introducir unha nova propiedade: 'encargados', onde o valor introducido será o seguinte array:
['Juan','Francisco']

db.artigos.updateMany({id:6}, {$set: {encargados: ['Juan', 'Francisco']}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
## Base de datos de medicamentos
> Lembra que utilizar un booleano ou un valor *1* ou *0*, realiza a tarefa de mostrar ou ocultar o valor buscado.

- Crea unha base de datos onde crear a seguinte colección:

use medicamentos
switched to db medicamentos

load('medicamentos.js')
true

```js
db.medicamentos.insertOne(
  {
    _id: 1,  
    nome: 'Sertal',
    laboratorio: 'Roche',
    precio: 5.2,
    cantidade: 100  
  }
)
db.medicamentos.insertOne(
  {
    _id: 2,  
    nome: 'Buscapina',
    laboratorio: 'Roche',
    precio: 4.10,
    cantidade: 200 
  }
)
db.medicamentos.insertOne(
  {
    _id: 3,  
    nome: 'Amoxidal 500',
    laboratorio: 'Bayer',
    precio: 15.60,
    cantidade: 100 
  }
)
db.medicamentos.insertOne(
  {
    _id: 4,  
    nome: 'Paracetamol 500',
    laboratorio: 'Bago',
    precio: 1.90,
    cantidade: 200 
  }
)
db.medicamentos.insertOne(
  {
    _id: 5,  
    nome: 'Bayaspirina',
    laboratorio: 'Bayer',
    precio: 2.10,
    cantidade: 150 
  }
)
db.medicamentos.insertOne(
  {
    _id: 6,  
    nome: 'Amoxidal jarabe',
    laboratorio: 'Bayer',
    precio: 5.10,
    cantidade: 50 
  }
)

```
### Atopar con ... e uso de 
{
- Mostra todos os documentos onde só se visualicen o _id e o laboratorio}
db.medicamentos.find({}, {_id: 1, laboratorio: 1})
[
  { _id: 1, laboratorio: 'Roche' },
  { _id: 2, laboratorio: 'Roche' },
  { _id: 3, laboratorio: 'Bayer' },
  { _id: 4, laboratorio: 'Bago' },
  { _id: 5, laboratorio: 'Bayer' },
  { _id: 6, laboratorio: 'Bayer' }
]
- Mostra os medicamentos onde laboratorio sexa 'Roche' e onde o precia sexa menor a 5.
db.medicamentos.find({laboratorio: 'Roche', precio: {$lt: 5}})
[  
  {
    _id: 2,
    nome: 'Buscapina',
    laboratorio: 'Roche',
    precio: 4.1,
    cantidade: 200
  }
]

- Mostra os medicamentos onde laboratorio sexa 'Roche' ou onde o precio sexa maior a 5.
 db.medicamentos.find({laboratorio: 'Roche', precio: {$gt: 5}})
[  
  {
    _id: 1,
    nome: 'Sertal',
    laboratorio: 'Roche',
    precio: 5.2,
    cantidade: 100
  }
]
- Mostra os medicamentos onde laboratorio non sexa 'Bayer'.
db.medicamentos.find({laboratorio: {$ne:'Bayer'}})
[  
  {
    _id: 1,
    nome: 'Sertal',
    laboratorio: 'Roche',
    precio: 5.2,
    cantidade: 100
  },
  {
    _id: 2,
    nome: 'Buscapina',
    laboratorio: 'Roche',
    precio: 4.1,
    cantidade: 200
  },
  {
    _id: 4,
    nome: 'Paracetamol 500',
    laboratorio: 'Bago',
    precio: 1.9,
    cantidade: 200
  }
]

- Mostra os medicamentos onde laboratorio sexa 'Bayer' e onde cantidade non sexa 100.
db.medicamentos.find({laboratorio: 'Bayer', cantidad: {$ne: 100}})
[  
  {
    _id: 3,
    nome: 'Amoxidal 500',
    laboratorio: 'Bayer',
    precio: 15.6,
    cantidade: 100
  },
  {
    _id: 5,
    nome: 'Bayaspirina',
    laboratorio: 'Bayer',
    precio: 2.1,
    cantidade: 150
  },
  {
    _id: 6,
    nome: 'Amoxidal jarabe',
    laboratorio: 'Bayer',
    precio: 5.1,
    cantidade: 50
  }
]

- Mostra os laboratorios que sexan 'Bayer' e o precio menor que 6, pero só debes mostrar o nome e o laboratorio
db.medicamentos.find({laboratorio: 'Bayer', precio: {$lt: 6}}, {nome: 1, laboratorio: 1})
[
  { _id: 5, nome: 'Bayaspirina', laboratorio: 'Bayer' },
  { _id: 6, nome: 'Amoxidal jarabe', laboratorio: 'Bayer' }
]


### Eliminar

- Borra os documentos da colección onde laboratorio sexa "Bayer" ou onde precio sexa menor a 3.
db.medicamentos.deleteMany({laboratorio: 'Bayer', precio: {$lt:3}})
{ acknowledged: true, deletedCount: 1 }

### Modificar

- Cambia a cantidade 200 a todos os medicamentos de 'Roche' onde o precio sexa maior a 5.

 db.medicamentos.updateMany({laboratorio: 'Roche', precio: {$gt: 5}}, {$set: {cantidad: 200}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}