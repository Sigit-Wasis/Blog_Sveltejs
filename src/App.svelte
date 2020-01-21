<svelte:head>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
</svelte:head>

<script>
    // Import Components Navigasi
	import  { Collapse, Navbar, NavbarToggler, NavbarBrand, Nav, NavItem, NavLink } from 'sveltestrap';
    // Import Components Jumbroton
    import { Button, Jumbotron } from 'sveltestrap';

    // Import Card 
    import {
        Container, Card, CardBody, CardFooter, CardHeader,CardImg, CardSubtitle, CardText, CardTitle
    } from 'sveltestrap';

    // Menu Handling ketika Menu di Kecilkan
	let isOpen = false;

	function handleUpdate(event) {
    	isOpen = event.detail.isOpen;
	}

    // Integrasi API Konten Tunggal
    let items;
    $: fetch( `https://training.awpramono.web.id/blog/content/summary/latest/`+"?fresh="+(""+Math.floor(Math.random() * 1000000)))
        .then(r => r.json()) 
        .then(data => {
        items = data;
    });
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
        <Button color="primary">Detail</Button>
    </p>
</Jumbotron>

<!-- Content awal Blog yang terintegrasi dengan API -->
{#if items}
<Jumbotron>
  <h1 class="display-4" style="cursor: pointer;">{items[0].title}</h1>
  <p class="lead">
    {items[0].description}
  </p>
  <Button>Selengkapnya</Button>
</Jumbotron>
{/if}

<!-- Content Card -->
<Container>
<Card body class="mb-3">
  <CardHeader>
    <CardTitle><h3 class="display-7">Judul Artikel</h3>
    </CardTitle>
  </CardHeader>
  <CardBody><CardText>
    <p>Isi Artikel ... </p> 
    </CardText>
  </CardBody>
</Card>
</Container>
