<template>

  <v-table v-if="getRatesResult.length > 0" id="rates_table">
    <thead>
    <tr>
      <th class="text-left">
        Unit
      </th>
      <th class="text-left">
        Give
      </th>
      <th class="text-left">
        Get
      </th>
    </tr>
    </thead>
    <tbody>
    <tr
      v-for="item in getRatesResult"
      :key="item.id"
    >
      <td class="unit_name">
        {{ item.exchange.name }}
        <!--<v-btn
            color="white"
            prepend-icon="mdi-cloud-upload"
            width="120"
            height="25"
            class="change_click_button"
        >
          Exchange
        </v-btn>-->
      </td>
      <td class="give">{{ item.from_rate}} <span class="from_currency">{{item.from_currency.name}}</span><br>
        <!--<span class="min"><b>Min:</b> {{item.min}}</span> |
        <span class="max"><b>Max:</b> {{item.max}}</span>-->
      </td>
      <td class="get">
        {{ item.to_rate}}<span class="to_currency">{{item.to_currency.name}}</span>
        <!--<span class="min"><b>Reserve:</b>{{ item.reserve}}</span>-->
      </td>
    </tr>
    </tbody>
  </v-table>
  <v-progress-linear
    v-else
    indeterminate
    color="primary"
  ></v-progress-linear>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "RatesTable",
  data () {
    return {
      desserts: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
        },
      ],
    }
  },
  computed: {
    ...mapGetters(["getRatesResult"]),
  },
}
</script>

<style scoped>
  span.from_currency, span.to_currency{
    font-size: 12px;
    color: #888888;
  }
  span.min, span.max{
    font-size: 12px;
    color: #888888;
  }
</style>
