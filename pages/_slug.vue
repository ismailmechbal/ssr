<template>
  <main>
    <h1>{{ data.name }} - {{ data.search }}</h1>
    <ul>
      <li v-for="(item, index) in data.regulation.results" :key="index">
        <h2>{{ item.name }}</h2>
        <h3>{{ item.type }} - {{ item.address }}</h3>
      </li>
    </ul>
  </main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      day: new Date().getDate(),
      month: new Intl.DateTimeFormat("en-US", { month: "long" }).format(
        new Date()
      ),
      year: new Date().getFullYear(),
    };
  },
  async asyncData({ params }) {
    const { data } = await axios.get(
      `http://localhost:3000/seo/${params.slug}`
    );
    return { data: data.data };
  },
  head() {
    return {
      title: `${this.data.name} Parking - Free Parking, Garage Deals &amp; Street Parking Rules, ${this.month} ${this.year} | SpotAngels`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: `${this.month} ${this.day}, ${this.year} - Find free parking in ${this.data.name}, compare rates of parking meters and garages in downtown ${this.data.name}, including for overnight parking, and check street parking rules. SpotAngels parking maps help you find cheap parking and get the best deals on garages in ${this.data.name}, ${this.data.state}.`,
        },
      ],
    };
  },
};
</script>
<style>
main {
  margin: 0 auto;
  width: 800px;
}
.title {
  text-align: center;
}
</style>
