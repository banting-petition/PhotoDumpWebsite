<script>
    import { browser } from '$app/environment';
    let user = null;
    if (browser) {
        user = localStorage.getItem('user');
        if (!user) {
            location.href = '/';
        }
    }
    function logout() {
        if (browser) {
            localStorage.clear();
        }
        location.href = '/';
    }
</script>
{#if browser && user}
    <p>Logged in as: {user}</p>
    <button on:click={logout}>Log Off</button>
    {:else}
    <p>Loading... Please Wait...</p>
    {/if}