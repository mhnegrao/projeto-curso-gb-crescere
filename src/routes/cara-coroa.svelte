<script>
    import caracoroa2 from "./../../static/cara-coroa2.jpg";
    import jogarMoeda from "./../../static/jogar-moeda.jpg";
    import coinFlip from "./../../static/coin-flip-19.gif";
    import moedacara from "./../../static/cara.jpg";
    import moedacoroa from "./../../static/coroa.jpg";
    import {
        onMount
    } from "svelte";

    //elementos da página
    let elms = {
        botaoJogar: "",
        botaoNovoJogo: "",
        ladoMoeda: "",
        resultado: "",
        vencedor: "",
        imagemMoeda: "",
    };
    let moedas = {
        cara: moedacara,
        coroa: moedacoroa,
    };
    console.log(moedas);
    onMount(() => {
        elms.botaoJogar = obterElemento("#botaoJogar");
        elms.botaoNovoJogo = obterElemento("#botaoNovo");
        elms.ladoMoeda = obterElemento(".form-check-input");
        elms.resultado = obterElemento("#resultado");
        elms.vencedor = obterElemento("#vencedor");
        elms.imagemMoeda = obterElemento("#imagemMoeda");
        elms.botaoNovoJogo.style.display = "none";
    });

    function limpar() {
        elms.resultado.style.display = "none";
        elms.botaoNovoJogo.style.display = "none";
    }

    function obterElemento(elemento) {
        if (elemento[0] === "#") {
            return document.querySelector(elemento);
        }
        return document.querySelectorAll(elemento);
    }

    function obterDadosForm(e) {
        let form = e.target; //obtém o formulário atual de onde onsubmit foi disparado
        let objForm = new FormData(form);
        let entries = objForm.entries(); //obtem todos os campos de entrada do formulario
        const data = Array(Object.fromEntries(entries)); //transforma em um objeto {'chave':'valor'}
        return data;
    }

    function iniciarJogo(e) {
        e.preventDefault();
        let apostas = obterDadosForm(e);
        elms.resultado.style.display = "block";
        elms.imagemMoeda.src = coinFlip;

        setTimeout(function () {
            let ganhador = sortear(apostas);
            elms.vencedor.innerHTML =
                `<h4><strong>Ganhador<strong></h4><p style='color:blue;'> <strong>${ganhador.toUpperCase()}!!!</strong></p>`;
            elms.botaoNovoJogo.style.display = "block";
        }, 2000);
    }

    function sortear(aposta) {
        let result = Math.random() > 0.5 ? "cara" : "coroa";
        console.log(result);
        console.log(aposta);

        elms.imagemMoeda.src = moedas[result];
        return aposta[0].palpite == result ?
            aposta[0].primeiroJogador :
            aposta[0].segundoJogador;
    }

    // function sleep(ms) {
    //     return new Promise((resolve) => setTimeout(resolve, ms));
    // }

    // function wait(milliseconds) {
    //     const date = Date.now();
    //     let currentDate = null;
    //     do {
    //         currentDate = Date.now();
    //     } while (currentDate - date < milliseconds);
    // }
</script>

<svelte:head>
    <title>Jogo Cara ou Coroa</title>
</svelte:head>
<section id="conteudo">
    <div class="container">
        <div class="row">
            <h2>Cara Ou Coroa?</h2>
        </div>
        <div class="row">
            <div class="col">
                <figure>
                    <div id="imagem-logo">
                        <img src={caracoroa2} alt="Jogo cara ou coroa" />
                    </div>
                </figure>
            </div>
            <div class="col">
                <div id="resultado">
                    <div class="container">
                        <div class="row">
                            <div class="col">
                                <img id="imagemMoeda" src="" alt="" />
                            </div>
                            <div class="col">
                                <div id="vencedor" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="row">
            <div>Jogador Um escolhe o lado da moeda</div>
            <div id="formulario">
                <form on:submit|preventDefault={iniciarJogo}>
                    <div class="container">
                        <div class="row">
                            <div class="col col-sm-3">
                                <label for="jogador-um">Nome Jogador Um</label>
                                <input type="text" class="form-control" name="primeiroJogador" id="jogador-um" />

                                <div id="escolha" class="form-check">
                                    <div class="form-check-inline">
                                        <label class="checkbox-inline">
                                            <input type="radio" name="palpite" value="cara"
                                                class="form-check-input" />Cara
                                        </label>
                                    </div>
                                    <div class="form-check-inline">
                                        <label class="checkbox-inline">
                                            <input type="radio" name="palpite" value="coroa"
                                                class="form-check-input" />Coroa
                                        </label>
                                    </div>
                                </div>
                            </div>
                            <div class="col col-sm-3">
                                <label for="jogador-dois">Nome Jogador Dois</label>
                                <input type="text" class="form-control" name="segundoJogador" id="jogador-dois" />
                            </div>
                            <div class="row">
                                <div class="col">
                                    <div id="linha-botao">
                                        <figure>
                                            <img id="jogarMoeda" src={jogarMoeda} alt="Imagem jogar moeda" />
                                        </figure>
                                        <button id="botaoJogar" type="submit" class="btn btn-primary btn-lg">
                                            Jogar Moeda
                                        </button>
                                        <button id="botaoNovo" type="reset" class="btn btn-primary btn-lg"
                                            on:click={limpar}>
                                            Novo Jogo
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </form>
            </div>
        </div>
        <div class="row" />
    </div>

</section>

<style>
    label {
        font-size: 20px;
        color: rgb(235, 27, 8);
    }

    input[type="radio"] {
        -ms-transform: scale(1.5);
        /* IE 9 */
        -webkit-transform: scale(1.5);
        /* Chrome, Safari, Opera */
        transform: scale(1.5);
    }

    /* #titulo {
        font-size: 80px;
        font-weight: bolder;
        color: rgb(60, 235, 8);
    } */
    #imagem-logo {
        justify-content: flex-end;
    }

    #imagemMoeda {
        width: 150px;
        height: 110px;
    }

    #jogarMoeda {
        width: 100px;
        height: 100px;
    }

    #escolha {
        padding-top: 5px;
        padding-left: 30px;
    }

    #resultado {
        display: none;
    }

    #conteudo {
        display: flex;
        background-color: rgb(164, 195, 105);
        height: 500px;
        width: 800px;
        padding: 10px;
    }

    /* #vencedor {
    } */

    .checkbox-inline {
        color: rgb(39, 14, 185);
        font-size: 15px;
        padding-left: 2px;
        margin-left: 2px;
    }
</style>