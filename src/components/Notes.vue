<template>
    <div>
        <p>{{this.text}}</p>

        <ul>
            <li v-for="(note,index) in notes" :key="index">
                {{note}}
            </li>
        </ul>
        <input type="text" v-model="title" @keypress.enter="save">
        <p>Total Notes: {{totalNotes}}</p>
        
    </div>
</template>

<script>
import {useStore} from "vuex"
import { ref,computed } from "vue";
export default {
    created(){
      this.getText()
    },
    data(){
        return{
              text:"Add Notes"
        }
    },
    methods:{
      getText(){
          console.log(this.text)
      }
    },
    setup () {
        const store=useStore();
        const notes=computed(()=>store.state.notes);
        const totalNotes=computed(()=>store.getters.totalNotes);
        const title=ref("");

        function save(){
            store.dispatch("saveNote",title.value)
            title.value=""
        }

        return {
            totalNotes,
            notes,
            title,
            save
        }
    }
}
</script>

<style lang="scss" scoped>

</style>