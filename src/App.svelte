<script>

	import router from 'page';
	// Components
	import Header from './components/Header.svelte';
	import Home from './pages/Home.svelte';
	import Movie from './pages/Movie.svelte';
	import NotFound from './pages/NotFound.svelte';
  
	let page;
	let params;

	//hits Home when here
	router('/', () => page=Home)
	router('/movie/:id', (ctx, next)=> {
		params= ctx.params;
		next();
	}, ()=> page=Movie);

	router('/*', ()=> {page=NotFound});

	router.start();


 </script>
  

  <Header />
  
 <svelte:component this={page} {params} />


  
  <style>
	:global(body) {
	  font-family: 'Abel', sans-serif;
	  margin: 0;
	  padding: 0;
	  box-sizing: border-box;
	}
  </style>
  