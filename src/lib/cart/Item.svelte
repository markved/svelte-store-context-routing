<script>
    export let item;

    import AddItem from "./AddItem.svelte";
    import {getContext} from "svelte";
    import {key} from "../../external/external.js";
    const getExt = getContext(key);
</script>

<div class="item">
    <h2>{item}</h2>
    <h3>{getExt}</h3>
    <AddItem {item} />
</div>

<style>
    .item {
        width: 25%;
    }
</style>
