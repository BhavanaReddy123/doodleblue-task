<template>

  <div class="query-form card">
    <div class="card-content">
      <h2 class="title">Task Details</h2>
      <ui-input name="title"
                label="Title"
                v-model="title"
                v-validate="'required'"
                :error="getError('title')"
                @enter="validate"
      />
      <ui-input name="description"
                type="textarea"
                label="Description"
                v-model="description"
      />
      <ui-input name="date"
                type="date"
                label="Date"
                v-model="date"
                @enter="validate"
      />
      <div class="field is-grouped">
        <ui-button type="button"  class="update-btn" @click="validate">{{ id ? 'Update' : 'Add' }}</ui-button>
        <ui-button type="button" @click="cancel" class="cancel">Cancel</ui-button>
      </div>
    </div>
  </div>

</template>

<script>

function data () {
  return {
    id: null,
    title: '',
    description: '',
    date: null,
    message: '',
  }
}

export default {
  data () {
    return data()
  },

  computed: {
    values () {
      return this.$data
    }
  },

  methods: {
    show (data) {
      Object.assign(this, data)
      this.$el.querySelector('input').focus()
    },

    validate () {
      this.$validator
        .validate()
        .then(state => {
          if (state) {
            return this.submit()
          }
          this.message = 'Please complete the required fields!'
        })
    },

    submit () {
      this.$emit('submit', this.values)
      this.reset()
    },

    cancel () {
      this.$emit('cancel', this.values)
      this.reset()
    },

    reset () {
      Object.assign(this, data())
    },

    getError (name) {
      return (this.errors.first(name) || '').replace(/The .+ field/, 'This field')
    }
  }
}

</script>

<style lang="scss">
  .update-btn button {
    border: 1px solid #73d1da;
    background-color: #ffff;
    color: #18b7c0;
  }
  .cancel button {
    color: #CC0000;
    border: 1px solid #CC0000;
    background-color: #ffff;
  }
</style>
