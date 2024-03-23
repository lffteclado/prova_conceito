<template>
  <div class="w-full px-2">
    <ListItem v-for="contact in contacts" :key="contact.id">
      {{ contact.name }}
      <template #actions>
        <button @click="editContact(contact.id)">Editar</button>
        <button @click="removeContact(contact.id)">Excluir</button>
      </template>
    </ListItem>
  </div>
  <UIButton @click="addContact">Adicionar Contato</UIButton>
</template>
<script setup>
import { useRouter } from "vue-router";
const router = useRouter();

useHead({
  title: "Agenda",
  meta: [{ name: "description", content: "Agenda de contatos" },
  { name: "twitter:title", content: "Agenda.com" },
  {property: "og:title", content: "Agenda.com"}

],
});

const addContact = () => {
  router.push("/form");
};
const { contactList, deleteContact } = useContacts();
const contacts = contactList();

const editContact = (id) => {
  router.push({ path: "/form", query: { id } });
};

const removeContact = (id) => {
    deleteContact(id);
}
</script>
