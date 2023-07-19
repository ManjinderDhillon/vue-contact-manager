<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Add Contact</p>
        <p class="fst-italic">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis,
          officia!
        </p>
      </div>
    </div>
  </div>
  <div class="container mt-3">
    <div class="row">
      <div class="col-md-4">
        <form @submit.prevent="submitCreate">
          <div class="mb-2">
            <input
              type="text"
              class="form-control"
              v-model="contact.name"
              placeholder="Name"
            />
          </div>
          <div class="mb-2">
            <input
              type="text"
              class="form-control"
              v-model="contact.photo"
              placeholder="Photo URL"
            />
          </div>
          <div class="mb-2">
            <input
              type="email"
              class="form-control"
              v-model="contact.email"
              placeholder="Email"
            />
          </div>
          <div class="mb-2">
            <input
              type="number"
              class="form-control"
              v-model="contact.mobile"
              placeholder="Mobile"
            />
          </div>
          <div class="mb-2">
            <input
              type="text"
              class="form-control"
              v-model="contact.company"
              placeholder="Company"
            />
          </div>
          <div class="mb-2">
            <input
              type="text"
              class="form-control"
              v-model="contact.title"
              placeholder="Title"
            />
          </div>
          <div class="mb-2">
            <select
              v-model="contact.groupId"
              class="form-control"
              v-if="groups.length > 0"
            >
              <option value="">Select Group</option>
              <option :value="group.id" v-for="group of groups" :key="group.id">
                {{ group.name }}
              </option>
            </select>
          </div>
          <div class="mb-2">
            <input type="submit" class="btn btn-success" value="Create" />
          </div>
        </form>
      </div>
      <div class="col-md-4">
        <img :src="contact.photo" alt="" class="contact-img" />
      </div>
    </div>
  </div>
</template>
<script setup>
import { ContactServices } from "@/services/ContactServices";
import { onMounted, ref, reactive } from "vue";
const contact = reactive({
  name: "",
  photo: "",
  email: "",
  mobile: "",
  company: "",
  title: "",
  groupId: "",
});
const groups = ref([]);
const created = async () => {
  try {
    let response = await ContactServices.getAllGroup();
    groups.value = response.data;
  } catch (error) {
    console.log(error);
  }
};
const submitCreate = async () => {
  try {
    const response = await ContactServices.createContact(this.contact);
    if (response) {
      return this.$router.push("/");
    } else {
      return this.$router.push("/contacts/add");
    }
  } catch (error) {
    console.log(error);
  }
};
onMounted(() => {
  created();
});
</script>
