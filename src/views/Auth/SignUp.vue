<template>
  <v-container fluid class="fill-height">
    <v-row>
      <v-col cols="12" xs="12" sm="8" md="8" lg="7" class="ma-auto">
        <v-card class="" outlined :loading="loading">
          <v-row class="justify-space-between px-4 pt-6 pb-12">
            <v-col cols="12" sm="12" md="6">
              <v-card-title class="text-center">Streamly</v-card-title>
              <v-card-subtitle class="mb-5"
                >Buat akun Streamly kamu</v-card-subtitle
              >
              <v-card-text>
                <ValidationObserver ref="form" v-slot="{ handleSubmit, reset }">
                  <form
                    @submit.prevent="handleSubmit(signUp)"
                    @reset.prevent="reset"
                  >
                    <ValidationProvider
                      v-slot="{ errors }"
                      name="Email"
                      rules="required|email"
                    >
                      <v-text-field
                        v-model="email"
                        :error-messages="errors"
                        label="Email"
                        class="mb-3"
                        outlined
                        dense
                      ></v-text-field>
                    </ValidationProvider>
                    <ValidationProvider
                      v-slot="{ errors }"
                      name="Channel Name"
                      rules="required|min:3"
                    >
                      <v-text-field
                        v-model="channelName"
                        :error-messages="errors"
                        label="Nama Channel"
                        outlined
                        dense
                      ></v-text-field>
                    </ValidationProvider>
                    <v-row>
                      <v-col cols="6">
                        <ValidationProvider
                          v-slot="{ errors }"
                          name="Password"
                          rules="required|password:@confirm"
                        >
                          <v-text-field
                            v-model="password"
                            type="password"
                            :error-messages="errors"
                            label="Password"
                            outlined
                            dense
                          ></v-text-field>
                        </ValidationProvider>
                      </v-col>
                      <v-col cols="6">
                        <ValidationProvider
                          v-slot="{ errors }"
                          name="confirm"
                          rules="required"
                        >
                          <v-text-field
                            type="password"
                            v-model="confirmPassword"
                            :error-messages="errors"
                            label="Konfirmasi"
                            outlined
                            dense
                          ></v-text-field>
                        </ValidationProvider>
                      </v-col>
                    </v-row>
                    <div class="mt-6 d-flex justify-space-between">
                      <v-btn
                        text
                        small
                        class="pl-0 text-capitalize"
                        color="primary"
                        router
                        to="signin"
                        >Login saja</v-btn
                      >
                      <v-btn
                        type="submit"
                        class="danger"
                        :loading="loading"
                        depressed
                        >Daftar</v-btn
                      >
                    </div>
                  </form>
                </ValidationObserver>
              </v-card-text>
            </v-col>
            <v-col cols="5" class="align-self-center hidden-sm-and-down">
              <v-responsive>
                <svg width="188" height="365" viewBox="0 0 242 465" fill="none" xmlns="http://www.w3.org/2000/svg">
<g clip-path="url(#clip0_38_30)">
<path d="M103.833 175.733C104.007 175.733 104.216 175.733 104.389 175.733C104.355 175.629 104.32 175.524 104.32 175.42L162.248 142.474C212.323 113.986 229.872 50.1846 201.481 0L51.0827 85.5332L49.1715 86.6825C30.1284 101.902 26.1321 175.733 103.833 175.733Z" fill="url(#paint0_linear_38_30)"/>
<path d="M189.91 304.834C178.72 289.406 157.14 275.336 137.541 282.162L68.1799 322.247C18.2787 351.083 1.18162 414.989 29.9547 465L192.724 370.865L195.956 368.845C205.2 348.68 202.976 322.839 189.91 304.834Z" fill="url(#paint1_linear_38_30)"/>
<path d="M237.865 253.535C225.355 209.306 187.651 179.46 141.815 177.44L104.633 175.803C104.563 175.803 104.494 175.803 104.424 175.803C104.424 175.768 104.424 175.733 104.39 175.733C104.216 175.733 104.007 175.733 103.834 175.733C26.1322 175.733 30.1284 101.936 49.2063 86.6825C10.1124 111.131 -8.23571 157.589 3.50983 202.236C15.2554 246.883 54.0713 278.227 100.08 280.247L137.263 281.884C137.333 281.884 137.402 281.884 137.472 281.884C137.506 281.988 137.541 282.058 137.541 282.162C157.175 275.336 178.72 289.406 189.91 304.834C202.976 322.874 205.2 348.68 195.991 368.845C233.938 343.004 250.375 297.764 237.865 253.535Z" fill="url(#paint2_linear_38_30)"/>
</g>
<defs>
<linearGradient id="paint0_linear_38_30" x1="273.925" y1="31.2729" x2="-15.1738" y2="165.891" gradientUnits="userSpaceOnUse">
<stop offset="0.0256" stop-color="#DC3636"/>
<stop offset="0.7785" stop-color="#570D0D"/>
</linearGradient>
<linearGradient id="paint1_linear_38_30" x1="230.375" y1="300.106" x2="56.3683" y2="386.919" gradientUnits="userSpaceOnUse">
<stop offset="0.0256" stop-color="#702121"/>
<stop offset="0.7785" stop-color="#E62D2D"/>
</linearGradient>
<linearGradient id="paint2_linear_38_30" x1="0.683259" y1="140.528" x2="242.6" y2="315.432" gradientUnits="userSpaceOnUse">
<stop offset="0.0256" stop-color="#702121"/>
<stop offset="0.7785" stop-color="#E62D2D"/>
</linearGradient>
<clipPath id="clip0_38_30">
<rect width="242" height="465" fill="white"/>
</clipPath>
</defs>
</svg>

              </v-responsive>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'SignUp',
  data: () => ({
    email: '',
    channelName: '',
    password: '',
    confirmPassword: '',
    loading: false
  }),
  methods: {
    async signUp() {
      this.loading = true

      const data = await this.$store
        .dispatch('signUp', {
          email: this.email,
          channelName: this.channelName,
          password: this.password
        })
        .catch((err) => {
          this.loading = false
          const errors = err.response.data.error

          this.$refs.form.setErrors({
            'Email': errors.find((error) => {
              return error.field === 'email'
            })
              ? ['Email ini sudah ada']
              : null,
            'Channel Name': errors.find((error) => {
              return error.field === 'channelName'
            })
              ? ['Channel ini sudah ada']
              : null
          })
        })

      if (!data) return

      const user = await this.$store
        .dispatch('getCurrentUser', data.token)
        .catch((err) => console.log(err))

      if (!user) return
      this.loading = false
      this.$router.push({ name: 'Home' })
    }
  }
}
</script>

<style></style>
