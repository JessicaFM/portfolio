<script>
    export let dataIndex
    console.log(dataIndex)
    let topPosition = (dataIndex * 100) + '%';
    console.log(topPosition)
</script>

<section id="main" style="--top: {topPosition}">
    Hello
</section>

<style>
    #main {
        top: var(--top);
    }
</style>