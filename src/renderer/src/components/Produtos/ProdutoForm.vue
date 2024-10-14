<template>
  <form class="p-3 row g-3">
    <div class="col-md-6">
      <label for="inputEmail4" class="form-label">Email</label>
      <input id="inputEmail4" type="email" class="form-control" />
    </div>
    <div class="col-md-6">
      <label for="inputPassword4" class="form-label">Password</label>
      <input id="inputPassword4" type="password" class="form-control" />
    </div>
    <div class="col-12">
      <label for="inputAddress" class="form-label">Address</label>
      <input id="inputAddress" type="text" class="form-control" placeholder="1234 Main St" />
    </div>
    <div class="col-12">
      <label for="inputAddress2" class="form-label">Address 2</label>
      <input
        id="inputAddress2"
        type="text"
        class="form-control"
        placeholder="Apartment, studio, or floor"
      />
    </div>
    <div class="col-md-6">
      <label for="inputCity" class="form-label">City</label>
      <input id="inputCity" type="text" class="form-control" />
    </div>
    <div class="col-md-4">
      <label for="inputState" class="form-label">State</label>
      <select id="inputState" class="form-select">
        <option selected>Choose...</option>
        <option>...</option>
      </select>
    </div>
    <div class="col-md-2">
      <label for="inputZip" class="form-label">Zip</label>
      <input id="inputZip" type="text" class="form-control" />
    </div>
    <div class="col-12">
      <div class="form-check">
        <input id="gridCheck" class="form-check-input" type="checkbox" />
        <label class="form-check-label" for="gridCheck"> Check me out </label>
      </div>
    </div>
    <div class="col-12">
      <button type="submit" class="btn btn-primary">Sign in</button>
    </div>
  </form>
</template>
<script setup>
import 'bootstrap/dist/js/bootstrap.bundle.min.js'
</script>
