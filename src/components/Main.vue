<template>
  <form v-on:submit.prevent>
    <div class="mb-3">
      <label for="accountId" class="form-label">Account ID</label>
      <input type="text" class="form-control" v-model="accountId" />
    </div>
    <div class="mb-3">
      <label for="since" class="form-label">Since</label>
      <input type="date" class="form-control" v-model="since" />
    </div>
    <div class="mb-3">
      <label for="until" class="form-label">Until</label>
      <input type="date" class="form-control" v-model="until" />
    </div>
    <div class="mb-3">
      <label for="words" class="form-label">Search words</label>
      <input type="text" class="form-control" v-model="words" />
    </div>
    <button type="submit" class="btn btn-primary" v-on:click="search">Search</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      url: "https://twitter.com/search",
      accountId: "",
      since: "",
      until: "",
      words: "",
    };
  },
  methods: {
    search() {
      let query = `q=`
          + (this.accountId ? `from:${this.accountId} `: "")
          + (this.since ? `since:${this.since} ` : "")
          + (this.until ? `until:${this.until} ` : "")
          + `${this.words}`;
      query = encodeURI(query);
      const url = `${this.url}?${query}&src=typed_query&f=live`;
      window.open(url);
    }
  }
};
</script>