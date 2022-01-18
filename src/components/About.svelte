<script>
    export let dataIndex
    let topPosition = (dataIndex * 100) + '%';

</script>
<section style="--top: { topPosition }">
    About
</section>
<style>
    section {
        top: var(--top);
        background-color: red;
    }
</style>