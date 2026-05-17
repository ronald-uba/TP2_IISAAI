**PROMPT v.1**

Necesito un openapi.yaml (3.1) para una API de libros con Genres y Books.

recursos:  
  Genre   { id, title }  
  Book  { id, title, language, rank, genre_id}  

endpoints:  
  GET    /genres  
  POST   /genres  

  GET    /genres/{id}/books  
             entrada (query params - opcionales): 
                    page: int (opcional, por defecto 1) 
                    limit: int (opcional, por defecto 10) 
             salida 200 (OK):  
                    { id: int, title: string, language: string, rank: int|null, genre_id: int}  
             salida 400 (datos invalidos):  
                     {error: "title y language son requeridos"}  
              salida 404 (genre no existe):  
                      {error: "no se encontró el género {id}"}  

  POST   /genres/{id}/books  
            entrada (body):  
                     title: string, requerido  
                     language: string, requerido  
                     rank: int (1 a 3), opcional  
             salida 201 (creado):  
                     {id: int, title: string, language: string, rank: int|null, genre_id: int}  
             salida 400 (datos invalidos):  
                     {error: "title y language son requeridos"}  
              salida 404 (genre no existe):  
                      {error: "no se encontró el género {id}"}  

  DELETE /genres/{id}/book/{bookId}  
              salida 204 (no content):  
                       ninguna  
              salida 404 (recurso no existe):  
                       {error: "no se encontró el género {id} o el libro {bookId}" }  

abrilo en canvas para que podamos editarlo juntos  

**Prompt v2. agregando un endpoint de PUT en books/{bookid}**

agregale a yaml este endpoint sin modificar el resto de los endpoints creados antes:

PUT    /genres/{id}/book/{bookId}  
             entrada (body):  
                     title: string, requerido  
                     language: string, requerido  
                     rank: int (1 a 3), opcional  
             salida 200 (OK):  
                     { id: int, title: string, language: string, rank: int|null, genre_id: int }  
             salida 400 (datos inválidos):  
                     { error: "title y language son requeridos" }  
             salida 404 (recurso no existe):  
                     { error: "no se encontró el género {id} o el libro {bookId}" }  
