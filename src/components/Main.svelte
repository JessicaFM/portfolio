<script>
    export let dataIndex
    let topPosition = (dataIndex * 100) + '%';
</script>

<section id="main" style="--top: {topPosition}">
    Hello
</section>

<style>
    #main {
        top: var(--top);
    }
</style>