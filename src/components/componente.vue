<script setup>
    import { ref } from "vue";
    const input_tasks = ref([])
    const input_task = ref()
    const cont = ref(0)
    const colors = ["bg-red-400","bg-green-400"]
    function add() {
        input_tasks.value.push(input_task.value);
        input_task.value = ''
    }
    function show(){
        if(cont.value ===0){
            cont.value ++
            document.getElementById("papu").classList.remove("hidden")
        }else{
            cont.value --
            document.getElementById("papu").classList.add("hidden")
        }
    }
</script>
<template>
    <div class="h-full w-full">
        <div class="bg-slate-300 m-auto w-1/2 flex flex-col justify-center items-center p-10  select-none">
            <div class="">
                <input type="text" placeholder="escribe tareas" v-model="input_task" class="mr-8 p-3 rounded-xl">
                <button class="bg-white p-3 mr-8 rounded-xl" @click="add()">Agregar</button>
                <button :class="colors[cont]" class="rounded-xl p-3" @click="show()">Mostrar</button>
            </div>
            <div id="papu" class="hidden">
                <div
                    class="bg-amber-200 p-8 mt-8 rounded-xl"
                    v-for="(task,index) in input_tasks"
                    :key="index"
                >
                    {{ task }}
                </div>
            </div>
        </div>
    </div>
</template>