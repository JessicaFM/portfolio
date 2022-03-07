<script>
    import { afterUpdate, createEventDispatcher } from "svelte";

    export let currentIndex
    let currentColor
    let currentSecondary
    let upArrow = './assets/images/up-arrow.png';
    let hiddenUp = true
    let hiddenDown = false
    const dispatch = createEventDispatcher();

    updateColors();

    function updateColors() {
        if (currentIndex == 0) {
            currentColor = '#ffffff'
            currentSecondary = '#000000'
        } else if(currentIndex == 4) {
            currentColor = '#000000'
            currentSecondary = '#ffffff'
        }

        // Can do It better
        if(!currentIndex) {
            hiddenUp = true
            hiddenDown = false
        } else if(currentIndex) {
            hiddenUp = false
            if(currentIndex == 3) { 
                hiddenDown = true
            } else {
                hiddenDown = false
            }
        } 
    };

    function handleClick(state) {
        console.log("state", state)
        console.log("currentIndex", currentIndex)


        // I need to fix this
        if(!currentIndex || currentIndex < 0) {
            currentIndex = 0;
        }

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
  
        console.log("currentIndex", currentIndex)

        dispatch("goTo", { index: currentIndex })
    };

    afterUpdate(() => {
        updateColors();
    });
</script>

<ul class="custom-paginator" style="--theme-color: { currentColor }; --theme-secundary: { currentSecondary}">
    <li><button hidden={ hiddenUp } class="sc-prev" on:click={ () => handleClick('prev') }><img src="{upArrow}"/></button></li>
    <li><button hidden={ hiddenDown } class="sc-next" on:click={ () => handleClick('next') }><img src="{upArrow}"/></button></li>
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
            height: 40px;
            button {
                height: 40px;
                border: none;
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