<script context="module">
    export async function preload(page, session){
        if (session.auth == false){
            this.redirect(302, '/');
        }
    }
</script>

<script>
    import NewPost from '../components/NewPost.svelte';
</script>

<NewPost/>
