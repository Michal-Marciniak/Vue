<template>
    <div>
        <!-- @submit zamiast v-on:submit=$emit("AddTodo"), ponieważ najpierw -->
        <!-- tworzymy metodę AddTodo, a dopiero później za jej pomocą emitujemy event -->
        <form @submit="addTodo">
            <!-- v-model przechowuje na bieżąco to, co wpisaliśmy jako tytuł -->
            <input type="text" v-model="title" name="title" placeholder="Add todo...">
            <input type="submit" name="Submit" value="Add" class="btn">
        </form>
    </div>
</template>

<script>
// uuid tworzy unikalne id dla obiektu "w locie"
import uuid from 'uuid';

export default {
    name: "AddTodo",
    // data to funkcja która zwraca todos
    data() {
        return {
            // gdybyśmy chcieli zwracać takie dane
            // jak email, miasto etc. to wstawiałoby się tutaj
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            // zatrzymujemy domyślne zachowanie, aby od razu po dodaniu
            // todo nie zniknęło na stronie
            e.preventDefault();
            // tworzymy nowy obiekt
            const newTodo = {
                // uuid to funkcja, v4-używamy wersji czwartej
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            // Emitujemy funkcję add-todo
            // i nowo utworzony obiekt do rodzica
            this.$emit('add-todo', newTodo);
            // po tym jak wyemitujemy nowo utworzony obiekt,
            // czyścimy jego tytuł, żeby pokazał się znowu
            // placeholder
            this.title = '';
        }   
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
        font-weight: bold;
        font-size: 90%;
    }
</style>