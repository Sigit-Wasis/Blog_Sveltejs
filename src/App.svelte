<svelte:head>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
</svelte:head>

<script>
	import  { Collapse, Navbar, NavbarToggler, NavbarBrand, Nav, NavItem, NavLink } from 'sveltestrap';
	let isOpen = false;

	function handleUpdate(event) {
    	isOpen = event.detail.isOpen;
	}
	
	let name = 'world';
</script>

	<Navbar color="dark" dark expand="md">
	  	<NavbarBrand href="/">Blog</NavbarBrand>
	  	<NavbarToggler on:click={() => (isOpen = !isOpen)} />
	  	<Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
	    	<Nav class="ml-auto" navbar>
	      		<NavItem>
	         		<NavLink > Beranda </NavLink>
	      		</NavItem>
	      		<NavItem>
	         		<NavLink > Tentang Kami </NavLink>
	      		</NavItem>
	    	</Nav>
	  	</Collapse>
	</Navbar>

<h1>Hello {name}!</h1>