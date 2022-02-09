<script>
    import { afterUpdate } from "svelte";

    export let currentIndex
    let currentColor;
    let currentSecondary;
    updateColors();

    function updateColors() {
        if (currentIndex == 0 || currentIndex == 2) {
            currentColor = '#ffffff'
            currentSecondary = '#000000'
        } else {
            currentColor = '#000000'
            currentSecondary = '#ffffff'
        }
    };

    afterUpdate(() => {
        updateColors();
    });
    
</script>
<ul class="custom-paginator" style="--theme-color: { currentColor }; --theme-secundary: { currentSecondary}">
    <li><a dataIndex="0" href="#0" class="{currentIndex === 0 ? 'active' : ''}"></a></li>
    <li><a dataIndex="1" href="#1" class="{currentIndex === 1 ? 'active' : ''}"></a></li>
    <li><a dataIndex="2" href="#2" class="{currentIndex === 2 ? 'active' : ''}"></a></li>
    <li><a dataIndex="3" href="#3" class="{currentIndex === 3 ? 'active' : ''}"></a></li>
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
            a {
                padding: 5px;
                width: 2px;
                height: 2px;
                display: block;
                border: 1px solid var(--theme-color);
                border-radius: 50%;
                &.active {
                    background-color: var(--theme-color);
                }
            }
        }
    }
</style>