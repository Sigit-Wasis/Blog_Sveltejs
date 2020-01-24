<svelte:head>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
</svelte:head>

<script>
	import { Container,
    Breadcrumb, 
    BreadcrumbItem } from 'sveltestrap';
</script>

<Breadcrumb>
  <BreadcrumbItem>Beranda</BreadcrumbItem>
  <BreadcrumbItem active>Tentang Kami</BreadcrumbItem>
</Breadcrumb>
<Container>
  <h4>Tentang Kami</h4>
  <p>
    Blog latihan ini disusun sebagai proyek pendamping dari buku Cara Cepat Menguasai SVELTE (Proyek Blog). Tujuannya agar para pembaca bisa menguasai framework SVELTE ini secara hands on dengan melibatkannya ke dalam proyek secara langsung.
  </p>
</Container>