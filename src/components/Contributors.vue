<template>
  <b-container>
    <div class="text-center">
      <h1>Contributors</h1>
      <p>Thanks for helping in front-end community</p>
    </div>
    <br>
    <div>
      <b-row>
        <b-col class="contribute-item" cols="4">
            <div class="main-object">
            <b-media>
              <b-img slot="aside" :src="info.avatar_url" width="64" height="64" alt="placeholder" />
              <h6 class="mt-0">@{{info.login}}</h6>
              <a :href="info.html_url" target="_blank">
                <button type="button" class="btn btn-primary btn-sm">
                  Profile
                </button>
              </a>
            </b-media>
            </div>
        </b-col>
      </b-row>
    </div>
  </b-container>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Contributors', // this is the name of the component
  data () {
    return {
      info: null
    }
  },
  mounted () {
    axios
      .get('https://api.github.com/repos/moumen-soliman/frontend-helper/stats/contributors')
      .then(response => (this.info = response.data[0].author))
  }
}
</script>
<style lang="scss" scoped>
.container {
  height: 80vh;
}
.text-center {
  h1,
  p {
    color: #000
  }
}
.main-object {
  background: white;
  border-radius: 5px;
  padding: 5px;
  box-shadow: 5px 5px 5px #e5e5e5;
  h6 {
    color: rgba(0, 0, 0, 0.5);
  }
  span {
    @extend p;
  }
  .btn {
    float: right;
  }
  .media {
    display: flex;
    align-items: flex-start;
  }
  .media-body {
    flex: 1;
  }
}
</style>
