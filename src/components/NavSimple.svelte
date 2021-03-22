<script>
  export let segment;
  export let itemsMenu;
</script>

<section>
  <main>
    <nav>
      <ul>
        {#each itemsMenu as page}
          <li>
            <a
              aria-current={segment === page.link ? "page" : undefined}
              href={page.link}>{page.title}</a
            >
          </li>
        {/each}
      </ul>
    </nav>
  </main>
</section>

<style>
  section {
    padding: 15px;
   
   align-content: center;
  }
  main {
    text-align: center;
  }
  nav {
    padding: 15px;
    border-bottom: 1px solid rgba(35, 12, 87, 0.1);
    font-weight: 300;
    padding: 0 1em;
   
    color: rgb(8, 14, 3);
    
  }

  ul {
    margin: 0;
    padding: 0;
  }

  /* clearfix */
  ul::after {
    content: "";
    display: block;
    clear: both;
  }

  li {
    display: block;
    float: left;
  }
  a:hover{
    color:darkgoldenrod
  }

  [aria-current] {
    position: relative;
    display: inline-block;
  }

  [aria-current]::after {
    position: relative;
    content: "";
    width: calc(100% - 1em);
    height: 2px;
    background-color: rgb(208, 255, 0);
    display: block;
    bottom: -1px;
  }

  a {
    text-decoration: none;
    padding: 1em 0.5em;
    display: block;
  }
</style>
