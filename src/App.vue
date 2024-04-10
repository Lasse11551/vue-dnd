<template>
  <div id="app">
    <NavbarItem/>
    <main class="flexbox">
      
        <BoardItem 
        v-for="board in boards"
        :key="board.id"
        :id="board.id" 
        :header="board.header">
          <CardItem 
          v-for="card in cards[board.id]"
          :key="card.id"
          :id="card.id" 
          :draggable="true"
          :title="card.title"
          :description="card.description"
          >
          </CardItem>
        </BoardItem>

    </main>
    <div class="input-container">
      <input type="text" id="titleInput" v-model="newCardTitle" placeholder="Enter card title">
      <input type="text" id="descriptionInput" v-model="newCardDescription" placeholder="Enter card description">
      <button @click="addCard(newCardTitle, newCardDescription)">Add Card</button>
   </div>
  </div>
</template>

<script>
import BoardItem from './components/BoardItem.vue'
import CardItem from './components/CardItem.vue'
import NavbarItem from './components/NavbarItem.vue'

export default {
  name: 'App',
  data() {
    return {
      boards: [
        {id: 'board-1', header: 'Backlog' },
        {id: 'board-2', header: 'To Do' },
        {id: 'board-3', header: 'Doing' },
        {id: 'board-4', header: 'Testing' },
        {id: 'board-5', header: 'Done' },
      ],
      cards: {
        'board-1': [
          {id: `card-${Date.now()}`, title: 'Css', description: 'Do css'},  
          {id: `card-${Date.now()}`, title: 'Vue', description: 'Do vue'},
          {id: `card-${Date.now()}`, title: 'Java', description: 'Do java'},
          {id: `card-${Date.now()}`, title: 'Typescript', description: 'Do typescript'},
          {id: `card-${Date.now()}`, title: 'Design', description: 'Do design'}
        ],
        'board-2': [],
        'board-3': [],
        'board-4': [],
        'board-5': []
      }
    }
  },
  components: {
    BoardItem,
    CardItem,
    NavbarItem
  },
  methods: {
    addCard(title, description) {
      if(!title.trim() || !description.trim()) {
        alert('Both title and description are required')
        return;
      }
      const newCardId = `card-${Date.now()}`;
      const newCard = {
        id: newCardId,
        title: title,
        description: description
      };
      this.cards['board-1'].push(newCard);
      this.newCardTitle = '';
      this.newCardDescription = '';
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

body{
  background-color: white;
}

.flexbox {
  display: flex;
  justify-content: space-between;
  width: 100%;
  overflow: hidden;
  margin: 0 auto;
  padding: 15px;
}

.flexbox .board {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 300px;
  min-height: 600px;
  height: auto;
  background-color: bisque;
  padding: 15px;
  border-radius: 20px;
}

.flexbox .board .card {
  padding: 15px 25px;
  background-color: white;
  cursor: pointer;
  margin-top: 15px;
  border-radius: 10px;
}
.flexbox .board .card:hover {
  background-color: #ccc;
  transition: 0.7s;
}

.input-container {
  display: flex;
  flex-direction: column;
  align-items: center; /* Center align the items horizontally */
  gap: 10px; /* Spacing between elements */
  margin: 20px; /* Margin around the container for some spacing from other elements */
}

.input-container input[type="text"],
.input-container button {
  width: 20%; 
  padding: 8px; /* Padding inside the input fields and button for better touch */
  border: 1px solid #ccc; /* A light grey border for the inputs and button */
  border-radius: 4px; /* Rounded corners for the inputs and button */
}

.input-container button {
  background-color: bisque; /* A nice blue background for the button */
  color: black; /* White text color for the button */
  cursor: pointer; /* Cursor indicates the button is clickable */
}

.input-container button:hover {
  background-color: rgb(240, 198, 147); 
  transition: 0.7s;
}
</style>
