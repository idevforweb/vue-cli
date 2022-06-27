<template>
    <!-- closeModal will be a custom event -->
    <!-- used .self 'event modifier' option: clicking only on .backdrop will close the Modal and not any else within div -->
    <div class="backdrop" @click.self="closeModal">
        <!-- modal class is static class / binded sale :class is dynamic class set up  -->
        <!-- if binded 'sale class', has a theme that equals sales, it will pick up the styles for that class -->
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <!-- rendering slot content -->
            <!-- Will render deualt content h1 and p from app.vua -->
            <slot>This defualt content will only show, if i didnt have the h1 and p elements.</slot>
            <div class="actions">
                <!-- by creating slots with the links name, we can show the content of v-slot's -->
                <slot name="links"></slot>
            </div>
            
        </div>
    </div>
</template>

<script>
export default {
    // exporting dynamic content from App.vue <Modal/> tag
    props: ['theme'],
    methods: {
        closeModal() {
            // Creating custom emit event to use .backdrop to close to modal
            // named it 'close'
            // emit event will be named 'close'
            // this event communicates with <Modal/> and will choose the modals 'toggleModal' method 
            this.$emit('close')
        }
    }
}
</script>

<style>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%
    }
    h1 {
        color:aqua;
    }
    .modal .actions {
        text-align: center;
        margin: 30px 0 10px 0;
        color: #333;
    }
    .modal .actions a {
        color:  #333;
        padding:  8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }
    /* Styling for dynamic modal sale class */

    .modal.sale {
        background-color: crimson;
        color:white;
    }
    .modal.sale h1 {
        color: white;
    }
</style>