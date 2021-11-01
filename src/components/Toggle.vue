<template>
    <div id="togglerDiv" aria-hidden="true">
        <span id="modeText">
            {{mode}} mode
        </span>
        <label class="toggle">
            <!-- Toggle.js component does the following: 
            - if mode === dark then checkbox is checked if not then it's not checked
            - this is the visual effect rather than the functionality
            - functionality is found in App.vue method Toggle
            - @change calles toggle method which changes mode between light and dark
            -->
            <input 
                type="checkbox" 
                :checked="(mode === 'dark') ? 'checked' : false" 
                @change="$emit('toggle')"
            />
            <span class="toggler round"> </span>
        </label>
    </div>
</template>

<script>
export default {
    props:['mode']
}
</script>