<script>
    export let contact
    let initialname = contact.name
</script>

<style>
    .contact-card{
        box-shadow: 0 2px 8px rgba(0,0,0,0.26);
        max-width: 30rem;
        border-radius: none;
        margin: 1rem 0;
    }
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .thumb{
        width: 33%;
        height: 100%;
    }
    .thumb-placeholder{
        background: #ccc;
    }
    img{
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
    .user-data{
        width: 67%;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
    h1{
        font-size: 1.25rem;
        font-family: 'Robert Slab', sans-serif;
    }
    h2{
        font-size: 1rem;
        font-weight: normal;
        color: #5a5a5a;
    }
    .description{
        border-top: 1px solid #ccc;
        padding: 1rem;
    }
</style>

<div class="contact-card">
    <header>
        <div class="thumb" class:thumb-placeholder="{!contact.image}">
            <img src={contact.image} alt={contact.name} />
        </div>
        <div class="user-data">
            <h1>{contact.name} / {initialname}</h1>
            <h2>{contact.title}</h2>
        </div>
    </header>
    <div class="description">
        <p>{@html contact.description}</p>
    </div>
</div>
