<template>
  <div>
    <header class="heading">
      <div class="result" v-if="$route.params.id">
        <h1 v-if="searching">
          Searching for <span class="specific">"{{ $route.params.id }}"</span>
        </h1>
        <h1 v-else>
          Search Results for
          <span class="specific">"{{ $route.params.id }}"</span>
        </h1>
      </div>
      <div class="search" v-else>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          version="1.1"
          id="Capa_1"
          x="0px"
          y="0px"
          viewBox="0 0 512.005 512.005"
          style="enable-background:new 0 0 512.005 512.005;"
          xml:space="preserve"
        >
          <g>
            <g>
              <path
                d="M505.749,475.587l-145.6-145.6c28.203-34.837,45.184-79.104,45.184-127.317c0-111.744-90.923-202.667-202.667-202.667    S0,90.925,0,202.669s90.923,202.667,202.667,202.667c48.213,0,92.48-16.981,127.317-45.184l145.6,145.6    c4.16,4.16,9.621,6.251,15.083,6.251s10.923-2.091,15.083-6.251C514.091,497.411,514.091,483.928,505.749,475.587z     M202.667,362.669c-88.235,0-160-71.765-160-160s71.765-160,160-160s160,71.765,160,160S290.901,362.669,202.667,362.669z"
              />
            </g>
          </g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
          <g></g>
        </svg>
        <input
          type="text"
          placeholder="Search for photo"
          name="search"
          v-model="result"
          @keyup.enter.prevent="submit"
        />
      </div>
    </header>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        result: "",
        display: false,
      };
    },
    computed: {
      searching() {
        return this.$store.state.searching;
      },
    },
    methods: {
      submit() {
        this.display = true;
        // this.$store.dispatch("getAllPictures", this.result);
        this.$router.push(`/search/${this.result}`);
      },
    },
  };
</script>
<style lang="scss" scoped>
  * {
    --primary-blue: #dde2e9;
    --dark-blue: #283a5a;
  }

  .heading {
    height: 20rem;
    background-color: var(--primary-blue);
    display: grid;
    place-items: center;

    & .search {
      display: flex;
      background-color: white;
      border-radius: 5px;
      padding: 1rem;
      width: 70%;
      margin: auto;

      & input {
        border: none;
        outline: none;
        width: 100%;
        margin-left: 1rem;
      }
      & input::placeholder {
        color: var(--primary-blue);
      }
      & svg {
        height: 1.5rem;
        fill: #cecece;
      }
    }
    .result {
      color: var(--dark-blue);
      width: 70%;
      // h1 {
      //   margin: 0 0.5rem;
      // }
      & .specific {
        opacity: 0.5;
      }
    }
  }
</style>
