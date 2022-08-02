<template>
  <v-card elevation="1" shaped class="pa-5">
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-row>
        <v-col cols="12" class="col-md-4 col-lg-4">
          <v-text-field
            v-model="name"
            :counter="10"
            :rules="nameRules"
            label="Name"
            required
          ></v-text-field>
        </v-col>
        <v-col cols="12" class="col-md-4 col-lg-4">
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>
        <v-col cols="12" class="col-md-4 col-lg-4">
          <v-select
            v-model="select"
            :items="items"
            :rules="[(v) => !!v || 'Item is required']"
            label="Item"
            required
          >
          </v-select>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <v-checkbox
            v-model="checkbox"
            :rules="[(v) => !!v || 'You must agree to continue!']"
            label="Do you agree?"
            required
          ></v-checkbox>

          <v-btn
            :disabled="!valid"
            color="primary"
            class="mr-4"
            @click="validate"
          >
            Validate
          </v-btn>

          <v-btn color="error" class="mr-4" @click="reset">
            {{ buttons.reset }}
          </v-btn>

          <v-btn color="warning" @click="resetValidation">
            Reset Validation
          </v-btn>

        </v-col>
      </v-row>
    </v-form>
  </v-card>
</template>
<script>
import Capslock from "../news/Capslock.vue";
export default {
    data: () => ({
        valid: true,
        name: "",
        nameRules: [
            (v) => !!v || "Nome é obrigatório",
            (v) => (v && v.length <= 10) || "O nome não pode ter menos que 10 caracteres",
        ],
        email: "",
        emailRules: [
            (v) => !!v || "E-mail is required",
            (v) => /.+@.+\..+/.test(v) || "O E-mail é obrigatório",
        ],
        select: null,
        items: ["Item 1", "Item 2", "Item 3", "Item 4"],
        checkbox: false,
        buttons: {
            reset: "Limpar",
        },
    }),
    methods: {
        validate() {
            this.$refs.form.validate();
        },
        reset() {
            this.$refs.form.reset();
        },
        resetValidation() {
            this.$refs.form.resetValidation();
        },
    },
    components: { Capslock }
}
</script>
