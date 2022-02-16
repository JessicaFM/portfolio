<script>
    import { afterUpdate, onMount } from "svelte";

    export let currentIndex
    let currentColor;
    let currentSecondary;
    updateColors();

    function updateColors() {
        if (currentIndex == 0) {
            currentColor = '#ffffff'
            currentSecondary = '#000000'
        } else if(currentIndex == 4) {
            currentColor = '#000000'
            currentSecondary = '#ffffff'
        }
    };

    function handleClick(state) {
        if(state == 'prev') {
            currentIndex = currentIndex - 1;
            if(currentIndex < 0) {
                currentIndex = 4;
            }
        } else {
            currentIndex = currentIndex + 1;
            if(currentIndex > 4) {
                currentIndex = 0;
            }
        } 
    };

    afterUpdate(() => {
        updateColors();
    });

    let upArrow = './assets/images/up-arrow.png';
    
</script>
<ul class="custom-paginator" style="--theme-color: { currentColor }; --theme-secundary: { currentSecondary}">
    {#if currentIndex != 0}
    <li><a class="sc-prev" on:click={ () => handleClick('prev') }><img src="{upArrow}"/></a></li>
    {/if}
    {#if currentIndex != 4}
    <li><a class="sc-next" on:click={ () => handleClick('next') }><img src="{upArrow}"/></a></li>
    {/if}
</ul>
<style lang="scss">
    .custom-paginator {
        position: absolute;
        right: 10px;
        top: 50%;
        z-index: 5;
        list-style: none;
        margin: 0;
        padding: 0;
        li {
            padding: 0;
            text-align: center;
            padding: 5px 0;
            margin-bottom: 10px;
            a {
                height: 40px;
                &.sc-next {
                    img {
                        transform: rotate(180deg);
                    }
                }
                img {
                    width: 40px;
                }
            } 
        }
    }
</style>