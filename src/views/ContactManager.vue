<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success font-bold">
          Contact Manager
          <router-link to="/contacts/add" class="btn btn-success btn-sm"
            ><i class="fa fa-plus-circle"> </i>New</router-link
          >
        </p>
        <p class="fst-italic">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus
          doloremque voluptate nam alias, error magni, laudantium in officia
          dicta nihil ad nobis vel dignissimos ex praesentium corrupti sit quo
          eaque.
        </p>
        <form>
          <div class="row">
            <div class="col-md-6">
              <div class="row">
                <div class="col">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Search Name"
                  />
                </div>
                <div class="col">
                  <input type="Submit" class="btn btn-outline-dark" />
                </div>
              </div>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
  <!-- Loading -->
  <div v-if="loading">
    <div class="container">
      <div class="row">
        <div class="col">
          <SpinnerComponent />
        </div>
      </div>
    </div>
  </div>
  <!-- Error -->
  <div v-if="!loading && errorMessage">
    <div class="container mt-3">
      <div class="row">
        <div class="col">
          <p class="h4 text-danger fw-bold">{{ errorMessage }}</p>
        </div>
      </div>
    </div>
  </div>
  <div class="container mt-3" v-if="contacts.length > 0">
    <div class="row">
      <div class="col-md-6" v-for="contact of contacts" :key="contact">
        <div class="card my-2 list-group-item-success shadow-lg">
          <div class="card-body">
            <div class="row align-items-center">
              <div class="col-sm-4">
                <img :src="contact.photo" alt="" class="contact-img" />
              </div>
              <div class="col-sm-7">
                <ul class="list-group">
                  <li class="list-group-item">
                    Name : <span class="fw-bold">{{ contact.name }}</span>
                  </li>
                  <li class="list-group-item">
                    Email :
                    <span class="fw-bold">{{ contact.email }}</span>
                  </li>

                  <li class="list-group-item">
                    Mobile :
                    <span class="fw-bold">{{ contact.mobile }}</span>
                  </li>
                </ul>
              </div>
              <div
                class="col-sm-1 d-flex flex-column justify-content-center align-items-center"
              >
                <router-link
                  to="/contacts/view/:contactId"
                  class="btn btn-warning my-1"
                >
                  <i class="fa fa-eye"></i>
                </router-link>
                <router-link
                  to="/contacts/edit/:contactId"
                  class="btn btn-primary my-1"
                >
                  <i class="fa fa-pen"></i>
                </router-link>
                <button class="btn btn-danger my-1">
                  <i class="fa fa-trash"></i>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ContactServices } from "@/services/ContactServices";
import SpinnerComponent from "@/components/SpinnerComponent.vue";
import { ref, onMounted } from "vue";

const loading = ref(false);
const contacts = ref([]);
const errorMessage = ref(null);

const fetchContacts = async () => {
  try {
    loading.value = true;
    const response = await ContactServices.getAllContacts();
    contacts.value = response.data;
    loading.value = false;
  } catch (error) {
    errorMessage.value = error;
    loading.value = false;
  }
};

onMounted(() => {
  fetchContacts();
});
</script>
