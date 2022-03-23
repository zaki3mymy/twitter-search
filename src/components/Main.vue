<template>
  <div class="py-5">
    <h2>Twitter search easier</h2>
    <p class="lead">For all twitter lovers...</p>
  </div>
  <div class="row">
    <div class="col-md-8">
      <form>
        <div class="mb-3">
          <label for="accountId">Account ID</label>
          <div class="input-group">
            <span class="input-group-text">@</span>
            <input type="text" class="form-control" v-model="accountId">
          </div>
        </div>
        <div class="row mb-3">
          <div class="col">
            <label for="since" class="form-label">Since</label>
            <input type="date" class="form-control" v-model="since" />
          </div>
          <div class="col">
            <label for="until" class="form-label">Until</label>
            <input type="date" class="form-control" v-model="until" />
          </div>
        </div>
        <div class="mb-3">
          <label for="words" class="form-label">Search words</label>
          <input type="text" class="form-control" v-model="words" />
        </div>
        <div class="col-12">
          <button type="submit" class="btn btn-primary" v-on:click="search">Search</button>
        </div>
      </form>
    </div>
  </div>
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