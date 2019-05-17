<template>
  <div>
    <b-col sm="6" offset="3">
      <b-form @submit="onSubmit">

        <b-form-group label-cols="4" label-cols-lg="2" label="Name" label-for="input-1">
          <b-form-input id="input-1" size="sm" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" label="Text" label-for="input-3">
          <b-form-input id="input-1" size="sm" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" label="Number" label-for="input-5">
          <b-form-input id="input-1" size="sm" type="number" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" label="Date" label-for="input-7">
          <b-form-input id="input-1" size="sm" type="date" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" label="Choice" label-for="input-9">
          <b-form-select :options="options"></b-form-select>
        </b-form-group>

        <b-button type="submit" variant="primary">Submit</b-button>
      </b-form>
    </b-col>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        options: [
          { value: 'a', text: 'a' },
          { value: 'b', text: 'b' }
        ]
      }
    }
  }
</script>
