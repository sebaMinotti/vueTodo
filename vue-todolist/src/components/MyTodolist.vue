<template>
    <div>
          <div class="container">
                    <div id="title">
                            <h1>{{ titolo }}</h1>
                            <span>{{ sottotitolo }}</span>
                            <div class="inserimento">
                                   <input @keyup.enter="nuovaFaccenda" v-model="newTodo" type="text" name="" placeholder="scrivi le tue faccende" id="">
                            </div>
                    </div>

                    <section id="containerTodo">
                        <div class="box">
                            <div class="titoloBox">
                                <h3>Lista cose da fare</h3>
                            </div>
                            <div class="boxlista container-fluid">
                                 <ul>
                                    <li   v-for="(faccenda, index) in listaFaccende" :key="index" ><div class="boxInput"><i class="fa-solid fa-check"></i><input type="radio" :checked="false" :name="'radioGroup'+index+ 'fatta'"  @change="faccendaFatta(index)" > <i class="fa-solid fa-trash"></i><input type="radio" :checked="false" :name="'radioGroup'+index+'nonFatta'" @change="faccendaNonFatta(index)"></div>{{ faccenda }}</li>
                                    
                                 </ul>
                            </div>
                           
                        </div>


                        <div class="box">
                            <div class="titoloBox">
                                <h3>Cose Fatte</h3>
                            </div>
                            <div class="boxlista container-fluid">
                                    <ul>
                                        <li v-for="(faccenda, index) in faccendeFatte" :key="index">{{ faccenda }}</li>
                                    </ul>
                                </div>
                        </div>

                        
                        <div class="box">
                            <div class="titoloBox">
                                <h3>Cose non Fatte</h3>
                            </div>
                            <div class="boxlista container-fluid">
                                    <ul>
                                        <li v-for="(faccenda, index) in faccendeNonFatte" :key="index">{{ faccenda }}</li>
                                    </ul>
                                </div>
                        </div>
                    </section>
          </div>
              
    </div>
</template>

<script>
    export default {
        name:'MyTodolist',
        data() {
            return {
                   newTodo:'',
                  titolo :'TodoList giornaliera',
                  sottotitolo:'completa quante piu faccende giornaliere',
                  listaFaccende:[],
                  faccendeFatte:[],
                  faccendeNonFatte:[]
            }
        },
        methods: {
            nuovaFaccenda:function(){
                this.listaFaccende.push(this.newTodo)
                this.newTodo=''
            },
            faccendaFatta:function(index){
                 if(!this.faccendeFatte.includes(this.listaFaccende[index])){
                     this.faccendeFatte.push(this.listaFaccende[index])
                     this.listaFaccende.splice(index,1)
                 }
            },
            faccendaNonFatta(index){
                if(!this.faccendeNonFatte.includes(this.listaFaccende[index])){
                    this.faccendeNonFatte.push(this.listaFaccende[index])
                    this.listaFaccende.splice(index,1)
                }
            }
            
        },
        mounted() {
            
        },
    }
</script>

<style  scoped>
.container{
    width: 100%;
    height: 40rem;
    margin: 1rem auto;
    background:#1d1d1d;
}
#title{
    width: 100%;
    height: auto;
    padding: 5px;
    position: relative;
}
.inserimento{
    width:30% ;
    height: 60%;
    position: absolute;
    right: 8px;
    top: 20px;
    border: none;outline: none;border-radius: 6px;padding: 5px;
}
.inserimento input{
    width: 100%;
    height: 100%;
    border: none;outline: none;
    padding: 5px;
}

#title h1{
    color:white;
    font-size: 1.8rem;
}
#title span{
    color: white;
}
#containerTodo{
    width: 100%;
    height: 34.5rem;
  display: flex;flex-direction: row;
    justify-content: center;
    
}
.box{
    width: calc(100% / 3 - 5px);
    height: 34rem;
    margin: 5px;
    background-color: grey;
    padding: 5px;
    box-shadow: 5px 5px 3px white;
}
.titoloBox{
    width: 100%;
    height: auto;
    padding: 10px;
    background-color: #1d1d1d;
    display: flex;align-items: center;
    color:white;
    
    
}
.titoloBox h3{
    font-size: 1.3rem;
}
.boxlista{
width: 100%;
height: auto;
min-height: 30rem;
padding: 5px;

margin-top: 10px;
}
li{
    
    width: 100%;
    height: 40px;
    margin-left: -20px;
    margin-top: 5px;
    background-color: white;list-style: none;
    display: flex;flex-direction: row;
    position: relative;
    align-items: center;
    border-radius: 6px;
    padding: 5px;
}
.boxInput{
    width: 25%;
    height: 80%;
    background-color:#1d1d1d;
    position: absolute;right: 2px;
    display: flex;flex-direction: row;align-items: center;
    border-radius: 6px;
}
 .boxInput i{
    margin-left: 10px;color: white;
    
}
.boxInput input{
    margin-left: 5px;
}



</style>