
<script>

export default {
    data() {
        return {
            tasks: 
                {
                    todo:"",
                    staus: false
                }
            ,
            text: "enter tasks to be completed.....",
            inputValue: "",
            detail: [],
            buttonStyle: {
                color: "white",
                fontWeight: "bolder",
                backgroundColor: "tomato",
            },
         

        }
    },
    methods: {
        addTask() {
            this.tasks.push({todo:this.inputValue,status:false})
            localStorage.setItem("task", JSON.stringify(this.tasks))
            this.inputValue = ""
        },
        enter() {
            this.tasks.push({todo:this.inputValue,status:false})
            localStorage.setItem("task", JSON.stringify(this.tasks))
            this.inputValue = ""
        },
        removeTask(task) {
            console.log(task)
            this.tasks.splice(task, 1)
            localStorage.setItem("task", JSON.stringify(this.tasks))

        },
       
toggle(task){
task.status = !task.status
localStorage.setItem("task", JSON.stringify(this.tasks))

}
    },

    mounted() {

        this.tasks = JSON.parse(localStorage.getItem("task")) || []
       
    },

}
</script>

<template>
    <div class="container">

        <div class="box">
            <h1>TODO LIST</h1>
            <input v-model="inputValue" type="text" placeholder="Enter Task" @keypress.enter="enter" />
            <button :disabled="(inputValue.length < 5)" @click="addTask"> Add Task </button>
            <ol>
                <li v-for="(task, index) of tasks" 
            
                :class=" {
                    strikeout:task.status
                } 
                 " class="static-class">
                    <div>
                        <input  type="checkbox" v-model="task.status"    @click="toggle(task)" />
                        {{ task.todo}}
                        <button :style="buttonStyle" @click="removeTask(index)"> Del</button>
                    </div>

                </li>
            </ol>

            <h3 v-if="(tasks.length === 0)"> {{ text }} </h3>

        </div>
    </div>
</template>



<style>
.container {

    background-color: rgb(231, 220, 201);
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}

.container>.box {
    width: 400px;
    padding: 1em;
}

.container>.box>input {
    padding: 7px;
    width: 70%;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
}

.container>.box>button {
    padding: 7px;
    margin-left: 4px;
}

.container>.box>ol {
    margin-top: 1em;
}

.container>.box>ol>li {
    font-weight: bold;
    background-color: white;
    margin-left: -1em;
    margin-bottom: 0.2em;
    padding: 9px;
}

.container>.box>ol>li>div {
    display: flex;
    justify-content: space-between;
}
</style>