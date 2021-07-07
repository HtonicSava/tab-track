<template>
    <div class="window">
        <div class="window__icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24"><path d="M12 2c5.514 0 10 4.486 10 10s-4.486 10-10 10-10-4.486-10-10 4.486-10 10-10zm0-2c-6.627 0-12 5.373-12 12s5.373 12 12 12 12-5.373 12-12-5.373-12-12-12zm-1.31 7.526c-.099-.807.528-1.526 1.348-1.526.771 0 1.377.676 1.28 1.451l-.757 6.053c-.035.283-.276.496-.561.496s-.526-.213-.562-.496l-.748-5.978zm1.31 10.724c-.69 0-1.25-.56-1.25-1.25s.56-1.25 1.25-1.25 1.25.56 1.25 1.25-.56 1.25-1.25 1.25z"/></svg>
        </div>
        <div class="window__text">
            <p>
                {{text}}  
            </p>
        </div>
        <div class="window__icon">
            <svg @click="close" xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24"><path d="M24 20.188l-8.315-8.209 8.2-8.282-3.697-3.697-8.212 8.318-8.31-8.203-3.666 3.666 8.321 8.24-8.206 8.313 3.666 3.666 8.237-8.318 8.285 8.203z"/></svg>
        </div>
    </div>
</template>

<script>
export default {
    name: 'hint',
    props: {
        text: String,
    },
    methods: {
        close(){
            this.$emit('closeHint')
        }
    }
}
</script>

<style scoped>
    .window{
        padding: 5px 10px;
        display: flex;
        justify-content: space-between;
        background-color: rgba(255, 255, 255, 0.575);
        border-radius: 5px;
        margin-top: 10px;
        margin-bottom: 10px;
        transition: 0.5s;
    }
    .window__icon:first-child{
        margin-right: 5px;
    }
    .window__icon:last-child{
        margin-left: 5px;
        cursor: pointer;
    }
</style>