<template lang="html">
  <div class="musiclist">
    <div class="panel hotsongs">
      <ul class="list">
        <router-link :key="index" :to="{name:'MusicPlay',params:{songid:item.song_id}}" tag="li" class="song" v-for="(item,index) in musicData.songlist">
        
          <div class="poster">
            <img :src="item.pic_big" :alt="item.title">
          </div>
          <div class="info">
              <div class="name">{{ item.title }}</div>
              <div class="author">{{ item.author }}</div>
          </div>
        </router-link>
      </ul>

    </div>
  </div>
</template>

<script>
export default {
  name:"singermusic",
  data(){
    return{
      fullscreenLoading:true,
      musicData:{
        songlist:[]
      }
    }
  },
  created(){
    const musiclistUrl = this.HOST + "/v1/restserver/ting?method=baidu.ting.artist.getSongList&tinguid="+ this.$route.params.singerid +"&limits=20&use_cluster=1&order=2"
    this.$axios.get(musiclistUrl)
    .then(res => {
      this.musicData = res.data
      this.fullscreenLoading = false
    })
    .catch(error =>{
      console.log(error);
    })
  }
}
</script>

<style scoped>

.musiclist{
  background-color: #fff;
  margin-top: 10px;
  padding: 10px 17px;
  padding-top: 0;
}

.layout.home .mod-lists .panel {
    border-top: 1px solid #eee;
    position: relative;
    top: -1px;
    display: none;
}

.list {
    word-wrap: break-word;
    -webkit-hyphens: auto;
    hyphens: auto;
    word-break: break-all;
}

.panel .list li {
    height: 55px;
    border-bottom: 1px solid #eee;
    padding-left: 0;
    display: -webkit-box;
    display: -webkit-flex;
    display: flex;
}

.list li.song {
    -webkit-box-pack: justify;
    -webkit-justify-content: space-between;
    justify-content: space-between;
    min-height: 55px;
    text-align: left;
    margin-top: 10px;
}

.panel .list li .poster {
    position: relative;
    width: 45px;
    margin-right: 8px;
}

.panel .list li .poster img {
    border: 1px solid #eee;
}

.list li .info {
    -webkit-box-flex: 1;
    -webkit-flex: 1;
    flex: 1;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}

.panel .list li .info .name {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-size: 16px;
    color: #333;
}

.panel .list li .info .author {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-size: 12px;
    color: #999;
    margin-top: 2px;
}
</style>
