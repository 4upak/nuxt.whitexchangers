<template >

  <v-text-field
    label="Get currency"
    v-model="ToSearchItem"
    @input="searchTo"
    id="to-list"
  >

  </v-text-field>
  <template
    v-for="(item, i) in getCurrenciesToLists"
  >
    <div
      :key="i"
      v-if="getCurrenciesToLists.length > 0 && item.active == true"
    >
      <v-card-title
        class="tag_title"
      >
        {{ item.name }}
      </v-card-title>
      <v-list
          density="compact"

      >
        <template v-for="(currency, j) in item.tag_currencies">
          <v-list-item
            :key="j"
            :value="currency"
            active-color="primary"
            @click="this.setToCode(currency.code_name); scrollTo()"
            v-if = "currency.active == true"
          >
            <v-list-item-title v-text="currency.name"></v-list-item-title>
          </v-list-item>
        </template>
      </v-list>

    </div>
  </template>



</template>

<script>

import { mapActions, mapGetters } from "vuex";
export default {
  name: "ToList",
  data: () => ({
    fromSelectedItem: 0,
    ToSearchItem: "",
  }),
  computed: {
    ...mapGetters(["getCurrenciesToLists"]),
  },
  methods: {
    ...mapActions(["setToCode"]),
    searchTo() {
      this.$store.dispatch("searchTo", this.ToSearchItem);
    },
    scrollTo() {
      document.getElementById("from-list").scrollIntoView( { behavior: "smooth" } );
    },
  },

}
</script>

<style scoped>

</style>
