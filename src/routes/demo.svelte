<script>
  import InputField from "../components/InputField.svelte";
  let campoEntrada = "Digite um texto aqui..";
</script>

<section id="content">
  <div class="container">
    <div id="objetivo">
      <div class="row">
        
        
        <h1>Iniciando</h1>
        <p>
          Vamos explorar as funcionalidades do Svelte e unificar aos
          conhecimentos com HTML, CSS e Javascript.
        </p>
        <p>Este trecho possui estilos simples CSS!</p>
      </div>
    </div>
    <div id="primeiro-passo">
      <div class="row">
        <h5>Utilizando componentes com reatividade</h5>
        <p>
          Criamos uma biblioteca de componentes básicos e iremos demonstrar
          aqui:
        </p>
      </div>
    </div>
    <div id="campo-entrada">
      <div class="row">
        <h6>Campo de entrada</h6>
      </div>
      <div class="row">
        <div class="form-inline">
          <label for="campo">Input com tag html</label>
          <input
            class="form-control"
            type="text"
            bind:value={campoEntrada}
            id="campo"
          />
        </div>
      </div>
    </div>
    <div id="svelte-componente">
      <p><strong>InputField componente Svelte</strong></p>
      <div class="row">
        <div class="col-sm-6">
          <InputField
            label="Primeiro campo"
            id="campo1"
            bind:valueInput={campoEntrada}
          />
        </div>
        <div class="col-sm-6">
          <InputField
            label="Segundo campo"
            id="campo1"
            bind:valueInput={campoEntrada}
          />
        </div>
      </div>
    </div>
    <div id="formulario-descricao" class="row">
      <h2>Formulários</h2>
      <p>
        Formulários são o coração de qualquer aplicativo, seja web, mobile ou
        desktop. É através dele que nossa aplicação interage com o usuário.
      </p>
      <p>
        Acesse o link: <a aria-current="form-demo" href="form-demo"
          >Formulários</a
        > para ver os exemplos.
      </p>
    </div>
  </div>
</section>

<style>
  * {
    margin: 0px;
  }
  a {
    text-decoration: underline;
    /* padding: 1em 0.5em;
    display: block; */
  }

  #objetivo {
    margin: 5px;
  }
  #campo-entrada {
    margin: 5px;
    background-color: rgb(203, 243, 216);
  }
  #campo-entrada > .row > .form-inline > label {
    padding-right: 10px;
  }

  #svelte-componente {
    margin: 5px;
    background-color: rgb(212, 183, 127);
  }
  #formulario-descricao {
    margin: 5px;
  }
  #primeiro-passo {
    margin: 5px;
  }
</style>
