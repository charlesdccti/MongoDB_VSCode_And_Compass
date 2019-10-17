Faça o que eu fiz na aula

Um índice no MongoDB nos ajuda a ter uma melhor performance nas consultas, vamos criar um índice para as categorias utilizando o comando no arquivo buscando-categorias.mongo:

db.artigos.createIndex({ categorias: 1 });

Podemos ver o índice criado utilizando o comando:

db.artigos.getIndexes();

E vamos também criar um índice para a slug, só que ele terá a propriedade de único, para que nenhum outro artigo na coleção tenha a mesma slug.

Em um arquivo chamado adicionando-indices-unicos.mongo vamos digitar o seguinte comando:

db.artigos.createIndex({ slug: 1}, { unique:true })