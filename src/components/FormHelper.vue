<template>
    <div class="form-helper">
        <h1>Please fill out the below form..</h1>
        <form name="InputForm">
            <div class="form-header">
                <slot name="form-header"></slot>
            </div>
            <div class="form-inputs">
                <slot name="form-inputs"></slot>
            </div>
            <div class="form-controls">
                <slot name="form-controls"></slot>
            </div>
        </form>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>

</style>
