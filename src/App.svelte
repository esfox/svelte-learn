<script>
import { Link, Route, Router } from 'svelte-navigator';

import Home from './pages/Home.svelte';
import Sandbox from './pages/Sandbox/Sandbox.svelte';

import Button from './ui/Button.svelte';

const routes =
[
	{ route: '/', label: 'Home' },
	{ route: '/sandbox', label: 'Sandbox' },
];

/** @param {Link.GetPropsParams}*/
const isActive = ({ href, isPartiallyCurrent, isCurrent }) =>
	(href === '/' ? isCurrent : isPartiallyCurrent || isCurrent) ? { class: 'active' } : {}

let theme = 'light';

</script>

<div id="app" class={`w-100 h-100 ${theme}`}>
	<Router primary={false}>

		<nav class="links pa4">
			{#each routes as { route, label }}
			<Link to={route.toLowerCase()} getProps={isActive}>
				<h2 class="pointer di hover-bg-near-white pa3 br-pill">
					{label}
				</h2>
			</Link>
			{/each}
		</nav>

		<Route path="/" >
			<Home/>
		</Route>
		<Route path="sandbox/*">
			<Sandbox/>
		</Route>
	</Router>

	<Button
		class="theme-switcher bottom-0 right-0 ma3"
		onClick={() => theme = (theme === 'light' ? 'dark' : 'light')}
	>
		🎨 Change Theme
	</Button>
</div>


<style type="text/scss">

	#app {
		--bg: white;
		--fg: black;
		color: var(--fg);
		background: var(--bg) !important;

		&.dark {
			--bg: #454545;
			--fg: #dddddd;
		}

		.links {

			:global(a) {
				color: var(--fg);
			}

			.active {

				h2 {
					background: var(--color-primary);
					color: white;
				}
			}
		}

		:global(.theme-switcher) {
			position: fixed !important;
		}
	}

</style>
