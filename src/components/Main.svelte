<script>
    export let dataIndex, colorPrimary
    console.log(colorPrimary);
//    let topPosition = (dataIndex * 100) + '%';
</script>

<section id="main" style="--text-color: {colorPrimary}">
    <div class="center-container">
        <div id="main-box" class="center-box">
            <div>Front-End</div> 
            <div>Dev</div>
        </div>
    </div>
</section>

<style lang="scss">
    #main {
        color: var(--text-color);
        #main-box {
            font-size: 6rem;
        }
    }
</style>