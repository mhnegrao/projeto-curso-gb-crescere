<script>
    import { get } from "lodash-es/get";
    import { getContext } from "svelte";
    import {FORM} from '../../node_modules/svelet-forms/Form.svelte';
    export let name = "";
    export let label = "";
    export let options; //um OBJETO

    /**propriedades extendidas do form*/
    const { touchField, setValue, values, errors, touched } = getContext(FORM);

    function onChange(event) {
        setValue(name, event.target.value);
    }
    function onBlur() {
        touchField(name);
    }
    if (Object.keys($$restProps).includes("value")) {
        setTimeout(() => setValue(name, $$restProps.value, false), 0);
    }
</script>

{#if label}
    <label for={name}>{name}</label>
{/if}
<section>
    {name}
    <select
        id={name}
        {name}
        value={get($values, name) && get($errors, name)}
        {...$$restProps}
    >
        <option value="" />
        {#each options as option}
            <option
                value={options.id}
                selected={get($values, name) === option.id}
                >{option.title}</option
            >
        {/each}
    </select>
    {#if get(touched, name) && get($erros, name)}
        <div class="message">{get($errors, name)}</div>
    {/if}
</section>

<style>
</style>
