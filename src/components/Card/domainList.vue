<template>
  <div class="container">
    <div class="row">
      <div class="col-md">
        <AppItemList
          title="Prefixos"
          v-bind:items="prefixes"
          v-on:addItem="addPrefix"
          v-on:deleteItem="deletePrefix"
        />
      </div>
      <div class="col-md">
        <AppItemList
          title="Sufixos"
          v-bind:items="sufixes"
          v-on:addItem="addSufix"
          v-on:deleteItem="deleteSufix"
        />
      </div>
    </div>

    <br />

    <h5>
      Domains
      <span class="badge badge-info">{{ domains.length }}</span>
    </h5>

    <div class="card domains">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="domain in domains" v-bind:key="domain.name">
            <div class="row">
              <div class="col-md">{{ domain.name }}</div>
              <div class="col-md text-right">
                <a v-bind:href="domain.url" target="_blank" class="btn btn-info">
                  <span class="fa fa-shopping-cart"></span>
                </a>
              </div>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import AppItemList from "./AppItemList";
export default {
  name: "DomainsList",
  components: {
    AppItemList
  },
  data() {
    return {
      prefixes: ["Air", "Jet", "Flight", "Pod"],
      sufixes: ["Hub", "Station", "Mart", "Try"]
    };
  },
  methods: {
    addPrefix(prefix) {
      this.prefixes.push(prefix);
    },
    addSufix(sufix) {
      this.sufixes.push(sufix);
    },
    deletePrefix(prefix) {
      this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
    },
    deleteSufix(sufix) {
      this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
    }
  },
  computed: {
    domains() {
      const domains = [];

      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          const name = prefix + sufix;
          const url = `https://checkout.hostgator.com.br/?a=add&sld=${name.toLowerCase()}&tld=.com.br&_ga=2.211999184.539753684.1570560389-2051749093.1570560389`;
          domains.push({
            name,
            url
          });
        }
      }

      return domains;
    }
  }
};
</script>

<style scoped>
  .domains .list-group {
    flex-direction: row;
    flex-wrap: wrap;
  }
  .domains .list-group-item {
    margin-left: 1rem;
    margin-bottom: 0.5rem;
    width:  calc(33% - 1rem);
  }
  .domains .list-groupo-item:nth-child(3n + 1) {
    margin-left: 0;
  }
  .domains .list-group-item + .list-group-item {
    border-radius: .3rem;
    border-top-width: 1px;
  }
</style>
