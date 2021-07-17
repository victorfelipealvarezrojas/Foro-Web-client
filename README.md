# Foro-Web-client
React-Redux-TypeScript-ApolloCient-Graphql

Foro web que permite realizar la publicación de un hilo previa autenticación del usuario que realizara el post y comentarios de otros usuarios sobre dicho post, ademas de 
eventos de like sobre los post de otros autores.

esta desarrollado con react y typescript, el backend que consume implementa graphQL por lo cual contiene toda la estructura necesaria para dicho consumo.
los estados de sesión globales los maneja con react-redux

no implementa variables de sesión local, estas son manejadas desde el backen por medio de redis asi que es importante realizar la configuración necesaria para que incluya las credenciales tanto en el playground de graphql("request.credentials": "include") como en el cliente:

const client = new ApolloClient({
  uri: 'aqui-el-servidor-graphql', 
  credentials: "include",
  cache: new InMemoryCache({
    //esta configuración deshabilita los resultados de la consulta para que no se almacenen en cachén y fuera de esto tengo que incluir no-cache en la consulta que lo requiera.
    resultCaching: false,
  })
});
