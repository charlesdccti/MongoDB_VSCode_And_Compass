# Faça o que eu fiz na aula

Lembre-se de instalar o Visual Studio Code e a extensão CosmosDB antes de continuar.

Para modelarmos o nosso blog no banco de dados, vamos criar um arquivo chamado inserindo-autores.mongo, neste arquivo, vamos digitar o comando para criar um autor:

    db.autores.insertOne({

        nome: "Gabriel Ferreira",

        descricao: "Desenvolvedor, instrutor e criador de conteúdo na Alura e grupo Caelum.",

        email: "gabs@caelum.com.br",

        senha: "gabs1234"

    })


Vamos executar este comando e para inserir o resto dos autores, vamos executar os comandos no arquivo inserir-autores.mongo.

Para adicionarmos os artigos, vamos primeiramente executar o comando update em um autor:

    db.autores.update({
        nome: "Gabriel Ferreira"
    }, {
        $set: {
            artigos: [
                {
                    slug: "projeto-caelum-nas-faculdades",
                    titulo: "Projeto Caelum nas Faculdades",
                    conteudo: "Por enquanto nós estamos indo apenas até faculdades de São Paulo e cidades próximas, 
                    mas nós podemos agendar uma palestra remota! Podemos fazer via Skype ou Hangouts, como eu já fiz 
                    com o pessoal da UNIFEOB:",
                    dataCriado: ISODate('2019-06-04')
                }
            ]
        }
    })


Para inserirmos os demais artigos, vamos executar os comandos dos arquivos inserir-artigos.mongo

Agora vamos criar um arquivo chamado buscando-artigos.mongo para fazer as buscas:
Buscando o artigo pela slug:

    db.autores.find({ "artigos.slug": "projeto-caelum-nas-faculdades" })


Buscando o artigo pela slug, mas retornando apenas o título e o conteúdo:

    db.autores.find({ "artigos.slug": "projeto-caelum-nas-faculdades"}, 
    { "artigos.titulo":1, "artigos.conteudo":1 })


Buscando todos os artigos do Gabriel Ferreira e retornando apenas o título e o conteúdo:

    db.autores.find({ "nome": "Gabriel Ferreira" }, 
    { "artigos.titulo":1 , "artigos.conteudo":1})


# O que aprendemos?

    - Vale a pena modelarmos o nosso banco de dados de acordo com a operação que fazemos com mais frequência
    - Aprender a migrar os dados é essencial para a modelagem.
    - É quase impossível acertar uma modelagem logo de primeira.
