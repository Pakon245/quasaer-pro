<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="id"
        label="Your id *"
        hint="id"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type id']"
      />
      <!--name-->
      <q-input
        filled
        v-model="name"
        label="Your name *"
        hint="Name and surname"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type name']"
      />
      <!--surname-->
      <q-input
        filled
        v-model="surname"
        label="Your surname *"
        hint="surname"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type surname']"
      />
      <!--language-->
      <q-input
        filled
        v-model="languag"
        label="ภาษา *"
        hint="ภาษา"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'กรุณาใส่ภาษา']"
      />
      <!--age-->
      <q-input
        filled
        type="number"
        v-model="age"
        label="Your age *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 100 || 'Please type a real age'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>

  </div>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()
    const name = ref(null)
    const surname = ref(null)
    const language = ref(null)
    const age = ref(null)
    const accept = ref(false)

    return {
      id,
      name,
      surname,
      language,
      age,
      accept,

      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'You need to accept the license and terms first'
          })
        }
        else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Submitted'
          })
        }
      },

      onReset () {
        HEAD
        id.value = null
        name.value = null
        surname.value = null

        id.value = ('6604101364')
        name.value = ('ภากร')
        surname.value = ('รักใหม่')
        language.value = ('ภาษาไทย')
        age.value = null

      }
    }
  }
}
</script>
