<script setup>
defineProps({
    inputedValue: {
        type: String,
    },
    label: {
        type: String,
    },
    fieldType: {
        type: String,
    },
});

const emit = defineEmits(['update:inputedValue']);

const changeInputedValue = (event) => {
    emit('update:inputedValue', event.target.value);
};
</script>

<template>
<textarea
    class="field field_textarea"
    v-if="fieldType === 'textarea'"
    :value="inputedValue"
    :placeholder="label"
    @input="changeInputedValue" 
></textarea>
<input 
    class="field field_input"
    v-else-if="fieldType === 'input'"
    :value="inputedValue"
    :placeholder="label"
    @input="changeInputedValue" 
    type="text"
>
</template>

<style scoped lang="scss">
.field {
    padding: 12px 16px;

    &::-webkit-scrollbar {
        width: 0;
    }

    &_textarea {
        height: 80px;
    }
}
</style>
