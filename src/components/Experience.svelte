<script>
    export let dataIndex
    let topPosition = (dataIndex * 100) + '%';

</script>
<section style="--top: { topPosition }">
    Experience
</section>
<style>
    section {
        top: var(--top);
        background-color: green;
    }
</style>