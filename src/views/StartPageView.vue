<script setup lang="ts"></script>

<template>
  <q-page>
    <div
      class="d-flex flex-column text-center justify-center"
      style="height: 90vh"
    >
      <div class="row">
        <p style="font-size: 5em">{{ $t("aboutMe") }}</p>
      </div>

      <div class="row">
        <div class="col-4">
          <div class="column items-start justify-start">
            <img
              src="../assets/portre.jpg"
              style="height: 40em; max-width: 30em"
            />
          </div>
        </div>

        <div class="column">
          <div class="row">
            <div class="col-8">
              <div class="column items-start">
                <div class="col">
                  <h5>{{ $t("name") }}</h5>
                </div>
                <div class="col">
                  <h5>tiborblascsok02@gmail.com</h5>
                </div>
                <div class="col">
                  <h5>Telefonszám</h5>
                </div>
              </div>
            </div>
            <div class="col-4">
              <div style="text-align: start">
                <div class="col">
                  <h5>{{ $t("skills") }}</h5>
                </div>
                <div class="col">
                  <h5>
                    {{ $t("web") }}
                    <br />
                    C#, PHP, TypeScript {{ $t("prof") }}
                    <br />
                    MySQL, NoSQL {{ $t("prof") }}
                    <br />
                    Angular, Vue.js {{ $t("prof") }}
                    <br />
                    Node.jg, Laravel {{ $t("prof") }}
                  </h5>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="row">
            <p style="font-size: medium; text-align: justify;"> {{ $t("aboutMsg") }} </p>
          </div>
      </div>
    </div>
  </q-page>
</template>

<style lang="scss" scoped></style>
