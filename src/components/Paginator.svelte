<script>
    export let current
    console.log(current)
</script>
<ul class="custom-paginator">
    <li><a dataIndex="0" href="#0" class="{current === '0' ? 'active' : ''}"></a></li>
    <li><a dataIndex="1" href="#1" class="{current === '1' ? 'active' : ''}"></a></li>
    <li><a dataIndex="2" href="#2" class="{current === '2' ? 'active' : ''}"></a></li>
    <li><a dataIndex="3" href="#3" class="{current === '3' ? 'active' : ''}"></a></li>
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
                border: 1px solid white;
                border-radius: 50%;
                &.active {
                    background-color: white;
                }
            }
        }
    }
</style>