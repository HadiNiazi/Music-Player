<template>
    <div>
        
        <h2>🎵 My Playlist</h2>

        <div class="form-inline">
            <input v-model="title" id="title" placeholder="🎵 Title">
            <input v-model="artist" id="artist" placeholder="🎤 Artist">
            <input v-model="audio" id="audio" placeholder="🔗 Audio URL">
            <button @click="saveSong">➕ Add Song</button>
        </div>

        <ul id="playlist" class="playlist"></ul>

    </div>
</template>

<script>
export default {    

    data() {
        return {

            title: '',
            artist: '',
            audio: '',
            
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
                audio: this.audio  
            });   

            this.clearForm();

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

</style>    