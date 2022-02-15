<script>
    export let dataIndex
    let topPosition = (dataIndex * 100) + '%';

</script>
<section style="--top: { topPosition }">
    Contact
</section>
<style>
    section {
        top: var(--top);
    }
</style>