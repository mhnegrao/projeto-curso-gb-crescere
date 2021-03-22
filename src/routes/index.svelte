<script>
  import NavSimple from "./../components/NavSimple.svelte";
  import successkid from "images/successkid.jpg";
  let menuItems = [
   
    {
      link: "demo",
      title: "Iniciando",
    },
    {
      link: "form-demo",
      title: "Exemplos de Formulários",
    },
  ];
</script>

<svelte:head>
  <title>Projeto Curso GB-Crescere</title>
</svelte:head>
<section>
  <div class="container">
    <h1>Projeto Curso Fullstack GB-Crescere!</h1>

    <figure>
      <img alt="Success Kid" src={successkid} />
      <figcaption>Sou Dev!</figcaption>
    </figure>
    <NavSimple itemsMenu={menuItems} />

    <h2>Olá Pessoal!!!!</h2>

    <p>
      Este site irá demosntrar a evolução dos meus conhecimentos adquiridos no
      curso <strong>Fullstack Gb-Crescere!</strong>
    </p>
    <p>
      Para uma melhor aproveitamento, estou utilizando SvelteJS/Sapper, um
      framework/compuilador que utiliza javascript puro.
    </p>
    <p>Por que utilizei este framework e quais suas vantagens?</p>
    <p>
      A resposta é que este framework é muito simples de utilizar, poderoso.
      Como estou iniciando agora no mundo web, ele tem uma curva de aprendizado
      muito pequena, pois venho do backend na plataforma dot.net utilizando C#.
      Utiliza javascript puro, o mesmo que estou tendo em aula e pela
      simplicidade da construção de componentes.
    </p>
    <p>
      Ainda não iniciei no curso a utilização do ReactJS mas este framework é
      tão simples que me encorajou a iniciar a construção de uma aplicação mas
      robusta.
    </p>
    <p>
      Todo o conteúdo que obtive e estou obtendo no curso será aplicado neste
      site
    </p>
    <p>
      Para maiores informações <a
        href="https://sapper.svelte.dev"
        target="_parent"
      >
        Svelte/Sapper
      </a>
    </p>
  </div>
</section>

<style>
  h1,
  figure,
  p {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    /* text-transform: uppercase; */
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  figure {
    margin: 0 0 1em 0;
  }

  img {
    width: 100%;
    max-width: 400px;
    margin: 0 0 1em 0;
  }

  p {
    margin: 1em auto;
  }
  h2 {
    margin: 1em auto;
    font-weigth: "bold";
  }
  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }
</style>
