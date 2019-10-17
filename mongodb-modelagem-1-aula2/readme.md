Faça o que eu fiz na aula


Vamos fazer a alteração da estrutura dos documentos, para isso vamos criar um arquivo com o nome de migrando-nova-estrutura.mongo e utilizar a agregação:

db.autores.aggregate([
    {
        $unwind: "$artigos"
    },
    {
        $project: {
            _id: 0,
            "autor.nome": "$nome",
            "autor.descricao": "$descricao",
            "autor.email": "$email",
            "autor.senha": "$senha",
            slug: "$artigos.slug",
            titulo: "$artigos.titulo",
            conteudo: "$artigos.conteudo",
            dataCriado: "$artigos.dataCriado"
        }
    },
    {
        $out: "artigos"
    }
])

db.autores.drop();

db.getCollectionNames();

Falta removermos a coleção antiga:

db.autores.drop();

E para vermos as coleções que temos, utilizamos o comando:

db.getCollectionNames();

Para adicionar as categorias dos nossos artigos, vamos criar um arquivo chamado adicionando-categorias.mongo:

db.artigos.updateOne({
    slug: "projeto-caelum-nas-faculdades"
}, {
    $set: {
        categorias: ["Inovação"]
    }
})

Para inserir as demais categorias, vamos executar os comandos do arquivo insercoes/inserir-comentarios.mongo

Vamos criar um novo arquivo chamado buscando-categorias.mongo para buscarmos pela categoria de programação, vamos utilizar o comando:

db.artigos.find({ categorias: "Programação" })

E podemos exibir as estatísticas de execução com o método explain.

db.artigos.find({ categorias: "Programação" }).explain("executionStats")
