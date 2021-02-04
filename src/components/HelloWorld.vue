<template>
      <v-row class="list-todo">
        <v-col cols="12" sm="12" md ="12" class="todo">
          <v-card class="card-todo">
              <v-flex class="conteiner">
                  <v-flex class="input-text">
                      <v-text-field outlined solo hide-details v-model="addText" dense style="width: 85%"></v-text-field>
                      <v-btn> ADICIONAR </v-btn>
                  </v-flex>
                  <v-flex class="content">
                       <v-list dense>
                          <v-subheader>A Fazer</v-subheader>
                          <v-list-item-group v-for="items in itemsTodo" :key="items.title" v-model="settings" multiple dense>
                              <v-list-item > 
                                <template v-slot:default="{ active }">
                                  <v-list-item-action >
                                    <v-checkbox :input-value="active"></v-checkbox>
                                  </v-list-item-action>
                                  <v-list-item-content>
                                    <v-list-item-title>{{items.title}}</v-list-item-title>
                                  </v-list-item-content>
                                  <v-list-item-action >
                                      <v-btn icon >
                                        <v-icon color="grey lighten-1">mdi-information</v-icon>
                                      </v-btn>
                                  </v-list-item-action>
                                </template>
                              </v-list-item>
                              <v-divider></v-divider>
                          </v-list-item-group>
                        </v-list>
                  </v-flex>
              </v-flex>
          </v-card>
        </v-col>
      </v-row>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  private itemsTodo: Array<any> = [];

  mounted() {
    this.itemsTodo.push({id: 1, title: 'Tarefa1'});
    this.itemsTodo.push({id: 2, title: 'Tarefa2'}); 
  }
}
</script>
<style scoped>
.list-todo{
  display: flex;
  flex-direction: row;
  justify-content: center;
  width: 90%;
  height: 300px;
}

.list-todo .todo{
  max-width:60%;
  height:100%;
  display:flex;
  flex-direction: column;
  border:dotted;
}

.list-todo .todo .card-todo{
  max-height: 100%;
  width: 100%;
  display:flex;
  flex-direction: column;
}

.list-todo .todo .card-todo .conteiner{ 
  display:flex;
  flex-direction: column;
  max-height: 100%;
  max-width: 100%;
}

.list-todo .todo .card-todo .conteiner .input-text{ 
   display:flex;
   flex-direction: row;
   max-width: 100%;
   max-height: 100%;
   border:dotted;
   align-items: center;
}

.list-todo .todo .card-todo .conteiner .content{ 
  display:flex;
  flex-direction: column;
  max-height: 100%;
  max-width: 100%;
  border:dotted;
  overflow-y: auto;
}  

.list-todo .todo .card-todo .conteiner .content::-webkit-scrollbar-track {
   background-color: #F4F4F4;
}
.list-todo .todo .card-todo .conteiner .content::-webkit-scrollbar {
   width: 5px;
    background: #F4F4F4;
}
.list-todo .todo .card-todo .conteiner .content::-webkit-scrollbar-thumb {
   background: silver;
}


</style>
