<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Edit Contact</p>
        <p class="fst-italic">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Cupiditate,
          tempora nam suscipit quaerat sint unde magnam quisquam inventore
          soluta culpa! Beatae, deserunt. Provident nihil corrupti et. Velit
          veritatis quisquam eaque!
        </p>
      </div>
    </div>
  </div>
  <div class="container mt-3">
    <div class="row">
      <div class="col-md-4">
        <form>
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="Name" />
          </div>
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="Photo URL" />
          </div>
          <div class="mb-2">
            <input type="email" class="form-control" placeholder="Email" />
          </div>
          <div class="mb-2">
            <input type="number" class="form-control" placeholder="Mobile" />
          </div>
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="Company" />
          </div>
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="Title" />
          </div>
          <div class="mb-2">
            <select class="form-control">
              <option value="">Select Group</option>
            </select>
          </div>
          <div class="mb-2">
            <input type="submit" class="btn btn-success" value="Update" />
          </div>
        </form>
      </div>
      <div class="col-md-4">
        <img
          src="https://cdn-icons-png.flaticon.com/512/219/219986.png"
          alt=""
          class="contact-img"
        />
      </div>
    </div>
  </div>
</template>
<script setup></script>
