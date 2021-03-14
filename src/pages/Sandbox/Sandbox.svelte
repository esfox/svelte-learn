<script>
  import { Route, Link } from 'svelte-navigator';

  import States from './States.svelte';
  import Bind from './Bind.svelte';

  /** @param {Link.GetPropsParams}*/
  const isActive = ({ href, isPartiallyCurrent, isCurrent }) =>
    (href === '/' ? isCurrent : isPartiallyCurrent || isCurrent) ? { class: 'active' } : {}
</script>

<div class="mh4 pa4">
  <h1 class="mv0">Trying out things 🤔</h1>
  <nav>
    <ul class="links flex ph0 mv3">
      {#each [ 'States', 'Bind' ] as route}
      <Link to={route.toLowerCase()} getProps={isActive}>
        <li class="hover-bg-green hover-white pa2 mr2 br4">
          <div class="ma0">{route}</div>
        </li>
      </Link>
      {/each}
    </ul>
  </nav>

    <Route path="states">
      <States/>
    </Route>

    <Route path="bind">
      <Bind/>
    </Route>
</div>

<style type="text/scss">

  .links {
    list-style-type: none;

    :global(a) {
      color: var(--fg);
    }

    .active li {
      background: var(--color-primary);
      color: white;
    }
  }

</style>
