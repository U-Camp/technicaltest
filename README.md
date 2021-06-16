
#  U Camp Technical Test
**🤟🏻Prueba técnica para los futuros instructores y facilitadores de U Camp 🤓💻**

📝El objetivo del test técnico es construir un Front-End y un Back-End que interactuen con una API externa.

👀Vamos a usar la API pública de **Mercado Libre**. De ella vamos a extraer publicaciones que luego vamos a guardar en tu propio back-end usando un caché. Para el Front-end vamos a desarrollar una serie de Componentes de React para poder mostrar e interactuar con las publicaciones antes mencionadas.

# Back-end

Usaremos el siguiente endpoint de Mercado Libre `https://api.mercadolibre.com/sites/MLA/search?q={query}`. Recibe un queryString con el parámetro `q` con un string que indica el keyword a buscar. La API retorna un JSON con la siguiente forma:

    {
      "site_id": "MLA",
      "query": "iphone",
      "paging": {},
      "results": [{
      	"id": "MLA851931164",
        "site_id": "MLA",
        "title": "iPhone 11 128 Gb Morado 4 Gb Ram",
        "seller": {},
        "price": 182240,
        ...
      }],
      "secondary_results": [
        ...
      ],
      "related_results": [
      	...
      ],
      "sort": {
        "id": "relevance",
        "name": "More relevant"
      },
      "available_sorts": [],
      "filters": [],
      "available_filters": []
    }

Podemos ver la documentación completa del endpoint en [este link](https://api.mercadolibre.com/sites/MLA/search?q=iphone).

Nuestro Back-End va a tener la ruta:

 - `/api/search`

## **`/api/search`**
Esta ruta recibe un queryString con un término de búsqueda. Por ejemplo: `/api/search?query=zapatillas`. Y debe retornar un arreglo de items de Mercado Libre con la forma:

    [
      {
          "id": "MLA785937833",
          "title": "Zapatillas Marca Rcn Ultraliviana Negra",
          "price": 1769,
          "currency_id": "ARS",
          "available_quantity": 200,
          "thumbnail": "http://http2.mlstatic.com/D_728833-MLA32445355209_102019-I.jpg",
          "condition": "new"
      },
      {
          "id": "MLA716347136",
          "title": "Zapatillas Ozono Skate Directo De Fábrica",
          "price": 1769,
          "currency_id": "ARS",
          "available_quantity": 200,
          "thumbnail": "http://http2.mlstatic.com/D_728833-MLA32445355209_102019-I.jpg",
          "condition": "new"
      }
    ]

Extra-Credit: En cada request de búsqueda, se deberá crear un caché, de tal manera que a la siguiente búsqueda no se use la API de Mercado Libre, si no que los datos se recuperen del caché. Tip: Usar un objeto (cada propiedad es al término de búsqueda y el valor de esa propiedad el arreglo de resultados).

## Front-End
Deberás crear una App en React con los siguientes componentes:

#### SearchBar
Un formulario **controlado** con un input de búsqueda, que dispare los requests a la API (a nuestro BACK-END, no a Mercado Libre).

#### Product Card
En este componente se muestra un producto en particular, debemos mostrar:

- su imagen
- su titulo
- su precio (con la moneda)
- su condición
- si tiene stock o no

#### Catálogo
Este componente va mostrar un arreglo de productos (obtenidos de la API) usando Product Card. Tambien debe posibilitar:

- Poder ordenar los productos en base a su precio, de forma ascendente o descendente.
- Poder filtrar por condición.
- Poder paginar los resultados de a 30 productos por página.

#### Notas
Crear un repo nuevo en tu github (privado o público) y compartémelo en el siguiente correo < nancy.nava@utel.edu.mx > una vez que hayas terminado.

Puedes usar cualquier librería extra para resolver este technical test, ya sea de front-end o de back-end. Te recomiendo usar alguna librería de front-end (Boostrap, Materialize, etc.).
