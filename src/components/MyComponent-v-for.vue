// https://www.youtube.com/watch?v=290wOr5jYzk
<template>
<p class="header">v-for, czyli renderowanie list</p>
  <div class="candidates">
    
    <div
      v-for="candidate in candidatesWithParty"
      :key="candidate.id"
      class="candidates__card"
    >
    <p>
        Name: {{ candidate.firstName }}
    </p>
    <p>
        Age: {{ candidate.age }}
    </p>
    <p v-show="candidate.party">
        Party: {{ candidate.party }}
    </p>
    <div v-show="candidate.opinionPool">
        Opinion pool:
        <progress max="10" :value="candidate.opinionPool"></progress>
    </div>
    
    
      
    </div>
  </div>
</template>

<script>
import { ref, computed } from "vue";
export default {
  name: "MyComponent-v-for",
  setup() {

    const candidatesWithParty = computed(()=>candidates.value.filter(({party}) => party))

    const candidates = ref([
              {
        id: Math.random(),
        firstName: "Ewa",
        lastName: "Nowak",
        age: 34,
        party: "PO",
        opinionPool: 3,
      },
      {
        id: Math.random(),
        firstName: "Elon",
        lastName: "Musk",
        age: 44,
        party: "Masters",
        opinionPool: 7,
      },
      {
        id: Math.random(),
        firstName: "John",
        lastName: "Doe",
        age: 44,
        party: "ABC",
        opinionPool: 4,
      },
      {
        id: Math.random(),
        firstName: "Mark",
        lastName: "Kowalsky",
        age: 44,
        party: "Lorem ipsum",
        opinionPool: 3,
      },
      {
        id: Math.random(),
        firstName: "Elon",
        lastName: "Musk",
        age: 44,
        party: "Masters",
        opinionPool: 7,
      },
      {
        id: Math.random(),
        firstName: "Elton",
        lastName: "John",
        age: 22,
        party: "Dolor sit",
        opinionPool: null,
      },
      {
        id: Math.random(),
        firstName: "Jan",
        lastName: "Kowalski",
        age: 45,
        party: "CDN",
        opinionPool: 9,
      },
    ]);

    return { candidates, candidatesWithParty };
  },
};
</script>

<style lang="scss" scoped>
.header {
  font-size: 19px;
  color: aqua;
}
.candidates {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 25px;

  &__card {
    background: #1f1f1f;
    padding: 30px;
  }
}
</style>