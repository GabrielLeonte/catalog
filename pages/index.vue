<template>
  <div class="customNavbar">
    <div>
      <aside class="column is-2 is-mobile ">
        <p class="menu-label is-hidden-touch">Bara de meniu</p>
        <ul class="menu-list">
          <li>
            <a style="pointer-events:none;">
              Note
            </a>
            <ul>
              <li>
                <a
                  :class="{ 'is-active': this.app === 'sem1' }"
                  @click="app = 'sem1'"
                >
                  Semestrul 1
                </a>
              </li>
              <li>
                <a
                  :class="{ 'is-active': this.app === 'sem2' }"
                  @click="app = 'sem2'"
                >
                  Semestrul 2
                </a>
              </li>
            </ul>
          </li>
          <li>
            <a
              :class="{ 'is-active': this.app === 'abs' }"
              @click="app = 'abs'"
            >
              Absente
            </a>
          </li>
        </ul>
      </aside>
    </div>
    <div class="table">
      <div v-if="app === 'sem1'">
        <!-- Semesterul 1 -->
        <div class="table-container ">
          <table class="table is-bordered">
            <tbody>
              <tr v-for="index in note">
                <th>{{ index.materie }}</th>
                <td v-for="nota in index.sem1">
                  <b>{{ nota.nota }} </b> pe {{ nota.data }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <!-- Semesterul 1 -->

      <!-- Semesterul 2 -->
      <div v-if="app == 'sem2'">
        <div class="table-container ">
          <table class="table is-bordered">
            <tbody>
              <tr v-for="index in note">
                <th>{{ index.materie }}</th>
                <td v-for="nota in index.sem2">
                  <b>{{ nota.nota }} </b> pe {{ nota.data }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <!-- Semesterul 2 -->

      <!-- Absente -->
      <div v-if="app == 'abs'">
        <div class="table-container ">
          <table class="table is-bordered">
            <tbody>
              <tr v-for="index in note">
                <th>{{ index.materie }}</th>
                <td v-for="nota in index.absente">
                  {{ nota }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <!-- Absente -->
    </div>
  </div>
</template>

<script>
export default {
  middleware: ["index"],
  data() {
    return {
      note: this.$store.state.elevData,
      app: "sem1"
    };
  }
};
</script>

<style>
.customNavbar {
  display: flex;
}
aside {
  margin-top: 3vh;
  min-width: 350px;
}
.table {
  margin-top: 2vh;
  overflow-y: auto;
}

/* width */
::-webkit-scrollbar {
  width: 10px;
}
/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #888;
}
/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>
