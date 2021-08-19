<template>
    <div id="container">
      
        <div id="content">
          <Songlist v-bind:songlist="songs" @addSongToList="addToPlaylist"/>
          <PlayList v-bind:PlaySonglist="playlists" @removeSongFromPlaylist="removeSong"/>
        </div>
      
    </div>
</template>

<script>
import Songlist from './components/Songlist.vue';
import PlayList from  './components/PlayList.vue';

export default {
    name: "App",
    components: {
      Songlist,
      PlayList,
    },
    data: function(){
      return {
        songs: [
            {id: 1, name: 'Peaches', singer: 'Justin Bieber feat. Daniel Caesar and Giveon'},
            {id: 2, name: 'Butter', singer: 'BTS'},
            {id: 3, name: 'Memories', singer: 'Maroon 5'},
            {id: 4, name: 'I Do not Care', singer: 'Ed Sheeran, Justin Bieber'},
            {id: 5, name: 'My heart will go on', singer: 'Celine Dion'},
            {id: 6, name: 'Lose You To Love Me', singer: 'Selena Gomez'},
            {id: 7, name: 'Rain on me', singer: 'Lady Gaga with Ariana Grande'},
            {id: 8, name: 'Bad habits', singer: 'Ed Sheeran'},
        ],
        playlists: [],
      }
    },
    methods: {
      addToPlaylist: function(song) {
        var index ;
        for(index = 0; index < this.songs.length; index++){
          if(song.id == this.songs[index].id){
            this.playlists.push(this.songs[index]);
            this.songs.splice(index,1);
            break;
          }
        }
      },
      removeSong: function(song){
        var index ;
        for(index = 0; index < this.playlists.length; index++){
          if(song.id == this.playlists[index].id){
            this.songs.push(this.playlists[index]);
            this.playlists.splice(index,1);
            break;
          }
        }
      },

   }
   
   
};
</script>

<style>

ul{
    display: flex;
    flex-wrap: wrap;
    list-style-type: none;
    padding: 0;
}

li{
    flex-grow: 1;
    flex-basis: 100px;
    text-align: center;
    padding: 10px;
    box-shadow:  1px 1px rgb(2, 2, 2);
}

h1{
    text-align: center;
}
#content{
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-column-gap: 40px;
  margin:auto;
}

</style>