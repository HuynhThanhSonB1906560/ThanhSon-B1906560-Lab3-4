<template>
    <div v-if="contact" class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="createContact"/>
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: ContactForm,
            message: "",
        };
    },
    methods: {
        async createContact(data) {
            ContactService.create(data);
            await alert("Thêm liên hệ thành công");
            this.$router.push({ name: "contactbook" });
        }
    },     
};
</script>