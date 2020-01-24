<svelte:head>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
</svelte:head>

<script>
    // Import Components Jumbroton
    import { Button, Jumbotron } from 'sveltestrap';

    // Import Card 
    import {
        Container, Card, CardBody, CardFooter, CardHeader,CardImg, CardSubtitle, CardText, CardTitle
    } from 'sveltestrap';

    // Integrasi API Konten Tunggal
    let items;
    $: fetch( `https://training.awpramono.web.id/blog/content/summary/latest/`+"?fresh="+(""+Math.floor(Math.random() * 1000000)))
        .then(r => r.json()) 
        .then(data => {
        items = data;
    });

    let articles;
    $: fetch( `https://training.awpramono.web.id/blog/content/summary/list/`+"?fresh="+(""+ Math.floor(Math.random() * 1000000)))
        .then(r => r.json()) 
        .then(data => {
          articles = data;
    });
</script>

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

<Container>
{#if articles}
    {#each articles as item }
        <Card body class="mb-3">
            <CardHeader>
                <CardTitle><h3 class="display-7">{item.title}</h3>
                </CardTitle>
            </CardHeader>
            <CardBody><CardText>
                <p>{item.description} </p> 
                </CardText>
            </CardBody>
        </Card>
    {/each}
{/if}
</Container>