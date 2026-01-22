<script setup>

    import {ref} from 'vue';
   
    let frombrancTest;
    let conflictLocal;
    let conflict;

    let to_do_liste = ref(false);
    let fait = ref(["fait1", "fait2", "fait3"])
    let ajout_do = ref("")
    let pas_fait = ref(["pas_fait1", "pas_fait2", "pas_fait3"])
    let ajout_ndo = ref("")
   
    function inversebool() {
      to_do_liste.value = !to_do_liste.value;
    }
   
    function ajout_liste_do() {
      fait.value.push(ajout_do.value);
    }
   
    function ajout_liste_ndo() {
      pas_fait.value.push(ajout_ndo.value);
    }
   
    function deplace_liste_ndo(element) {
      pas_fait.value.push(element);
      const index=fait.value.indexOf(element)
      fait.value.splice(index,1)
    }
   
    function deplace_liste_do(element) {
      fait.value.push(element);
      const index=pas_fait.value.indexOf(element)
      pas_fait.value.splice(index,1)
    }
   
    function effacer(element, lst) {
      const index=lst.indexOf(element)
      lst.splice(index,1)
    }
   
    </script>
   
    <template>
        
   
            <div v-if="to_do_liste">
               
                <h1>Choses faites</h1>
   
                <div id="test v-for">
                    <label for="ajout_a_la_liste">Ajout à la liste des choses faites : </label>
                    <input v-model="ajout_do" placeholder="À ajouter à la liste">
                    <button @click="ajout_liste_do">Ajouter</button>
   
                    <div v-for="i in fait">
                        {{ i }}
                        <button @click="deplace_liste_ndo(i)">Pas fait</button>
                        <button @click="effacer(i, fait)">Effacer</button>
                    </div>
                </div>
   
            </div>
   
            <div v-else>
   
                <h1>Choses pas faites</h1>
   
                <div id="test v-for">
                    <label for="ajout_a_la_liste">Ajout à la to-do liste : </label>
                    <input v-model="ajout_ndo" placeholder="À ajouter à la liste">
                    <button @click="ajout_liste_ndo">Ajouter</button>
   
                    <div v-for="i in pas_fait">
                      {{ i }}
                      <button @click="deplace_liste_do(i)">Fait</button>
                      <button @click="effacer(i, pas_fait)">Effacer</button>
                    </div>
                </div>
   
            </div>
       
   
        <button type="button" @click="inversebool">Voir l'autre liste</button>
     
      
   
     
   
    </template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Mountains+of+Christmas:wght@400;700&family=Quicksand:wght@400;500;600;700&display=swap');

h1 {
  color: #c41e3a;
  font-size: 2.2rem;
  font-family: 'Mountains of Christmas', cursive;
  text-align: center;
  margin-bottom: 25px;
  text-shadow: 2px 2px 4px rgba(196, 30, 58, 0.3);
}

h1::before {
  content: '🎄 ';
}

h1::after {
  content: ' 🎄';
}

label {
  color: #2e7d32;
  font-weight: 600;
  font-family: 'Quicksand', sans-serif;
  margin-right: 10px;
}

input {
  padding: 10px 18px;
  border: 2px solid #2e7d32;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.95);
  color: #1b5e20;
  font-size: 1rem;
  font-family: 'Quicksand', sans-serif;
  outline: none;
  transition: all 0.3s;
  margin-right: 10px;
}

input::placeholder {
  color: #81c784;
}

input:focus {
  border-color: #c41e3a;
  box-shadow: 0 0 15px rgba(196, 30, 58, 0.3);
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 12px;
  background: linear-gradient(135deg, #c41e3a, #8b0000);
  color: #fff;
  font-size: 0.95rem;
  font-weight: 700;
  font-family: 'Mountains of Christmas', cursive;
  cursor: pointer;
  transition: all 0.3s;
  margin: 5px;
  box-shadow: 0 4px 15px rgba(196, 30, 58, 0.3);
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(196, 30, 58, 0.5);
}

#test\ v-for {
  margin-top: 20px;
}

#test\ v-for > div {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 15px 20px;
  margin: 10px 0;
  background: rgba(255, 255, 255, 0.95);
  border: 3px solid #2e7d32;
  border-radius: 12px;
  color: #1b5e20;
  font-family: 'Quicksand', sans-serif;
  font-weight: 500;
  transition: all 0.3s;
  animation: slideIn 0.4s ease;
}

#test\ v-for > div::before {
  content: '🎁';
  font-size: 1.2rem;
}

#test\ v-for > div:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(46, 125, 50, 0.3);
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

#test\ v-for > div button {
  padding: 8px 15px;
  font-size: 0.85rem;
}

#test\ v-for > div button:first-of-type {
  background: linear-gradient(135deg, #2e7d32, #1b5e20);
}

#test\ v-for > div button:last-of-type {
  background: linear-gradient(135deg, #c41e3a, #8b0000);
}

button[type="button"] {
  display: block;
  margin: 30px auto 0;
  padding: 15px 30px;
  font-size: 1.2rem;
  background: linear-gradient(135deg, #2e7d32, #1b5e20);
}

button[type="button"]::before {
  content: '⛄ ';
}

button[type="button"]::after {
  content: ' 🎅';
}
</style>
