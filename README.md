// PASSO 1: Encontrar os botões e caixinhas que você criou no seu HTML
// Imagine que estamos dando nomes para os botões para o computador entender quem é quem.
const caixinhaNome = document.getElementById('nome');
const caixinhaemail = document.getElementById('email');
const caixinhasenha = document.getElementById('senha')
const botaoSalvar = document.getElementById('btn-salvar');

// PASSO 2: Definir o endereço de onde o seu Back-end vai morar no futuro
const enderecoDoBackEnd = "http://localhost:3000/api/perfil&quot";

// PASSO 3: Criar a ação de enviar os dados (A fiação elétrica)
function enviarDadosParaOBack() {

// Pegamos o que está escrito dentro das caixinhas e guardamos juntos
const dadosDoPerfil = {
    nome: caixinhaNome.value,
    email: caixinhaemail.value,
    senha: caixinhasenha.value
};

// Usamos o comando "fetch" (que significa "buscar/levar" em inglês)
// Ele vai pegar a nossa sacola de dados e levar até o endereço do Back-end
fetch(enderecoDoBackEnd, {
    method: "POST", // POST avisa: "Estou enviando algo novo para guardar!"
    headers: {
        "Content-Type": "application/json" // Avisa que estamos enviando um texto padrão de computador
    },
    body: JSON.stringify(dadosDoPerfil) // Transforma os dados em texto puro para viagem
})
.then(resposta => {
    // Se a viagem deu certo e o Back-end recebeu, avisa na tela!
    alert("Muito bem! Os dados foram enviados para o Back-end!");
})
.catch(erro => {
    // Se o Back-end estiver desligado (o que é normal agora, já que não criamos ele ainda), vai cair aqui:
    alert("O Front-end tentou enviar, mas o Back-end ainda está desligado.");
});
}

// PASSO 4: Ligar o botão da tela ao nosso código
// Dizemos ao computador: "Quando o usuário CLICAR no botaoSalvar, execute a função de enviar"
botaoSalvar.addEventListener("click", enviarDadosParaOBack);
