<template>
    <div>
        
        <h2>🎵 My Playlist</h2>

        <div class="form-inline">
            <input v-model="title" id="title" placeholder="🎵 Title">
            <input v-model="artist" id="artist" placeholder="🎤 Artist">
            <input v-model="audio" id="audio" placeholder="🔗 Audio URL">
            <button @click="saveSong">➕ Add Song</button>
        </div>

        <ul id="playlist" class="playlist">
            <li v-for="(song, index) in songs" :key="index">
                <div class="item">
                    <strong>{{ song.title }}</strong> by {{  song.artist }}
                </div>

                <div>
                    <button @click="playSong(song.audio)">Play</button>
                   
                    <button @click="toggleFavourite(index)">{{ song.favourite ? '💔 Unfavorite' : '❤️ Favorite' }}</button>
                    <button @click="removeSong(index)">Remove</button>
                     <button @click="pauseSong()">Pause</button>
                </div>
            </li>
        </ul>

    </div>
</template>

<script>
export default {    

    data() {
        return {

            title: '',
            artist: '',
            audio: '',
            favourite: false,
            currentSong: null,
            
            songs: []

        }
    },

    methods: {
        
        saveSong() {

            if (this.title == '' || this.artist == '' || this.audio == '') {
                alert('Please fill in all fields');
                return;
            }

            this.songs.push({
                title: this.title, 
                artist: this.artist,
                audio: this.audio,  
                favourite: this.favourite
            });   

            this.clearForm();

        },

        removeSong(index) {
            this.songs.splice(index, 1);
        },

        toggleFavourite(index) {
            this.songs[index].favourite = !this.songs[index].favourite;
        },

        playSong(audioUrl) {
            const audio = new Audio(audioUrl);
            this.currentSong = audio;
            audio.play();
        },

        pauseSong() {
            if (this.currentSong) {
                this.currentSong.pause();
            }
            else {
                alert('No song is currently playing');
            }
        },

        clearForm() {
            this.title = '';
            this.artist = '';
            this.audio = '';
        }
    }

}
</script>

<style scoped>
.item {
    color: white;
}
</style>    