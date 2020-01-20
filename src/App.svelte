<svelte:head>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
</svelte:head>

<script>
    // Import Components Navigasi
	import  { Collapse, Navbar, NavbarToggler, NavbarBrand, Nav, NavItem, NavLink } from 'sveltestrap';
    // Import Components Jumbroton
    import { Button, Jumbotron } from 'sveltestrap';

    // Menu Handling ketika Menu di Kecilkan
	let isOpen = false;

	function handleUpdate(event) {
    	isOpen = event.detail.isOpen;
	}
</script>
    
<!-- Kode untuk Menu Navigasi Blog -->
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
      		<NavItem>
         		<NavLink > Kontak </NavLink>
      		</NavItem>
    	</Nav>
  	</Collapse>
</Navbar>

<!-- Kode untuk Content awal Blog -->
<Jumbotron>
    <h5 class="display-3">Selamat Datang!</h5>
    <p class="lead">
        Kami ucapkan selamat datang di blog ini semoga bermanfaat.
    </p>
    <hr class="my-2" />
    <p>
      It uses utility classes for typography and spacing
      to space content out within the larger container.
    </p>
    <p class="lead">
        <Button color="primary">Selengkapnya</Button>
    </p>
</Jumbotron>