<template>
  <div class="cmp-service">
    <h1>Escolha o serviço:</h1>
    <div class="service-container">
      <div
        @click="setSelectedService(service)"
        class="card-service"
        v-for="service in services"
        :key="service.id"
      >
        <p class="name">Tipo: {{ service.name }}</p>
        <p class="price">Preço: {{ service.price.toFixed(2) }}</p>
        <p class="duration">Duração: {{ service.duration }}:00</p>
      </div>
    </div>
  </div>
</template>

<script>
import { mapMutations } from "vuex";
import "./Service.scss";
import axios from "axios";

export default {
  data() {
    return {
      services: [],
    };
  },
  mounted() {
    this.getServices();
  },
  methods: {
    ...mapMutations({
      setSchedulingInfo: "setSchedulingInfo",
      setActiveStep: "setActiveStep",
    }),
    async getServices() {
      try {
        const response = await axios.get("http://localhost:3000/services");
        this.services = response.data;
      } catch (error) {
        console.error(error);
      }
    },

    setSelectedService(service) {
      this.setSchedulingInfo({
        service: {
          name: service.name,
          price: service.price,
          duration: service.duration,
        },
      });
      this.setActiveStep(1);
    },
  },
};
</script>
