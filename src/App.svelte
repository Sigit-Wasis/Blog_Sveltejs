<svelte:head>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
</svelte:head>

<script>
    // Import Components Navigasi
	import  { Collapse, Navbar, NavbarToggler, NavbarBrand, Nav, NavItem, NavLink } from 'sveltestrap';
   
  // Menu Handling ketika Menu di Kecilkan
	let isOpen = false;

	function handleUpdate(event) {
    	isOpen = event.detail.isOpen;
	}

  // Import mainpage 
  import MainPage from './MainPage.svelte'

  let showHome = true;

  function handleAboutUs(event){
      showAboutUs = true;
      showHome = false;
      isOpen = false;
  }

  function handleHome(event){
      showAboutUs = false;
      showHome = true;
      isOpen = false;
  }  

</script>
    
<!-- Kode untuk Menu Navigasi Blog -->
<Navbar color="dark" dark expand="md">
  	<NavbarBrand href="/">Blog</NavbarBrand>
  	<NavbarToggler on:click={() => (isOpen = !isOpen)} />
  	<Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
    	<Nav class="ml-auto" navbar>
      		<NavItem>
         		<NavLink on:click={handleHome}> Beranda </NavLink>
      		</NavItem>
      		<NavItem>
            <NavLink on:click={handleAboutUs}> Tentang Kami </NavLink>
          </NavItem>
    	</Nav>
  	</Collapse>
</Navbar>

{#if showAboutUs}
<AboutUs />
{/if}

{#if showHome}
<MainPage />
{/if}