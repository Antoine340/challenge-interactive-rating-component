<script setup lang="ts">
import { ref } from 'vue'

const rating = ref(2)
const submitted = ref(false)
</script>

<template>
  <v-card
    v-if="!submitted"
    elevation="0"
    rounded="xl"
    color="hsl(213, 19%, 18%)"
    class="container pa-6"
  >
    <v-card-title>
      <v-avatar
        color="#2A323A"
        size="45"
        class="mb-8"
      >
        <v-img
          src="/images/icon-star.svg"
          alt="star"
          width="30%"
          height="30%"
        />
      </v-avatar>
      <h2>How did we do?</h2>
    </v-card-title>
    <v-card-text>
      <p class="opacity-6">
        Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!
      </p>
    </v-card-text>
    <v-card-actions
      class="d-flex flex-column"
    >
      <v-item-group
        v-model="rating"
        class="d-flex mb-8 w-100 justify-space-between rating"
      >
        <v-item
          v-for="n in 5"
          :key="n"
        >
          <template #default="{ toggle }">
            <v-btn
              :active="rating != null && rating + 1 >= n"
              color="hsl(217, 12%, 100%)"
              border
              icon
              height="50"
              width="50"
              class="rating-btn"
              @click="toggle"
            >
              {{ n }}
            </v-btn>
          </template>
        </v-item>
      </v-item-group>
      <v-btn
        :block="true"
        :color="rating == null ? 'hsl(217, 12%, 0%)' : 'hsl(25, 97%, 53%)'"
        variant="flat"
        class="text-white submit-btn"
        rounded="xl"
        :disabled="rating == null"
        @click="submitted = true"
      >
        SUBMIT
      </v-btn>
    </v-card-actions>
  </v-card>
  <v-card
    v-else
    elevation="0"
    rounded="xl"
    color="hsl(213, 19%, 18%)"
    class="container pa-6"
  >
    <v-card-title
      class="d-flex flex-column align-center mb-4"
    >
      <v-img
        src="/images/illustration-thank-you.svg"
        alt="thank you"
        width="150"
        height="150"
      />
      <v-chip
        class="result-chip px-6"
        color="hsl(213, 19%, 80%)"
      >
        <p>
          You selected {{ rating + 1 }} out of 5
        </p>
      </v-chip>
    </v-card-title>
    <v-card-text class="text-center">
      <h1 class="mb-4">
        Thank you !
      </h1>
      <p class="opacity-6">
        We appreciate you taking the time to give a rating. If you ever need more support, don't hesitate to get in touch!
      </p>
    </v-card-text>
  </v-card>
</template>

<style scoped lang="scss">
p {
  line-height: 1.5;
}
.container {
  max-width: 400px;
  color: white;
  background-image: linear-gradient(
          180deg,
          hsl(212deg 13% 19%) 0%,
          hsl(215deg 17% 14%) 25%,
          hsl(220deg 20% 12%) 99%
  );
}
.opacity-6 {
  opacity: 0.6;
}
.rating {
  .v-btn--active {
    background-color: hsl(217, 12%, 63%)!important;
    &:nth-last-child(1 of .v-btn--active) {
      background-color: hsl(25, 97%, 53%)!important;
    }
  }
  &-btn {
    background-color: hsl(210, 16%, 15%) !important;
    &:hover {
      background-color: hsl(217, 12%, 63%)!important;
    }
  }
}
.result-chip {
  .v-chip__content p {
    color: hsl(25, 97%, 53%)!important;
  }
}
.submit-btn {
  &:hover {
    background-color: hsl(0, 0%, 100%)!important;
    color: hsl(25, 97%, 53%)!important;
  }
}
</style>
