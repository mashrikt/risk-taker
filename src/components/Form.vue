<template>
  <div>
    <b-col sm="6" offset="3">
      <h3>{{name}}</h3>
      <hr>
      <b-form  @submit="onSubmit">
        <b-form-group label-cols="4" label-cols-lg="2" label="Name" label-for="input-1">
          <b-form-input id="input-1" size="sm" v-model="post_data.name" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" :label=text.display_name label-for="input-2">
          <b-form-input id="input-1" size="sm" v-model="post_data.data.description" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" :label=number.display_name label-for="input-3">
          <b-form-input id="input-1" size="sm" type="number" v-model="post_data.data.no_of_hair" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" :label=date.display_name label-for="input-4">
          <b-form-input id="input-1" size="sm" type="date" v-model="post_data.data.dob" required></b-form-input>
        </b-form-group>

        <b-form-group label-cols="4" label-cols-lg="2" :label=choice.display_name label-for="input-5">
          <b-form-select :options=choice.choices v-model="post_data.data.hair_color" required></b-form-select>
        </b-form-group>

        <b-button type="submit" variant="primary">Submit</b-button>
      </b-form>
    </b-col>
  </div>
</template>

<script>
  export default {
    props: {
      name: String,
      text: Object,
      number: Object,
      date: Object,
      choice: Object,
    },
    data () {
        return {
            post_data: {
                risk_type: 1,
                name: '',
                data: {
                  description: '',
                  no_of_hair: null,
                  dob: '',
                  hair_color: ''
                }
            }
        }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        fetch('http://157.230.35.253:3333/api/v1/risks/', {
          method: 'post',
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(this.post_data)
        })
        .then((response) => {
          alert("Response Status: " + response.status)
          return response.json()
        })
        .then((jsonData) => {
          alert("Response Data: " + JSON.stringify(jsonData))
        })
      },
    }
  }
</script>
