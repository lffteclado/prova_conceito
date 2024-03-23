<template>
  <div>
    <form>
      <UIInput label="Nome" type="text" v-model="contact.name" />
      <UIInput label="E-Mail" type="email" v-model="contact.email" />
      <UIInput label="Telefone" type="text" v-model="contact.phone" />
      <UIButton type="submit" @click="saveContact">Salvar Contato</UIButton>
    </form>
  </div>
</template>
<script setup>
import { onMounted } from 'vue';
import { useRoute } from 'vue-router';

const {createContact, getContact, updateContact} = useContacts();
const route = useRoute();
const router = useRouter();
const contact = reactive({
  id: 0,
  name: "",
  email: "",
  phone: "",
});
onMounted(() => {
    const id = route.query.id;
    if (id) {
        const {name, email, phone} = getContact(id);
        contact.id = id
        contact.name = name
        contact.email = email
        contact.phone = phone
    }
})
const saveContact = () => {
    if (contact.id) {
        updateContact(contact.id, contact)
    }else{
        createContact(contact)
    }
    router.push('/')
}
</script>
