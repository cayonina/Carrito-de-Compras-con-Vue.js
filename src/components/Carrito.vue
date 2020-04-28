<template>
    <div>
        <ul class="list-group">
            <!-- aqui en cada lista recore el arreglo  -->
            <li class="list-group-item" v-for="item in items" :key="item.id">
                {{item.titulo}} - ${{item.precio}}
                <button class="btn badge badge-danger float-right" @click="removerItem(item)">
                    Eliminar
                </button>
            </li>
        </ul>
        <div class="card p-3 my-5">
        <h4 class="text-center" >TOTAL: ${{total}} </h4>
        </div>
        <button :disabled="items.length === 0" @click="$emit('pagar')" class="btn btn-info form-control">Pagar Ahora</button>
    </div>
        
</template>


<script>
export default {
    name:'Carrito',
    // aqui recibe en los props el arreglo items con los prods. del carrito que viene de App.vue
    props: ['items'],
    computed:{
        total(){
            return this.items.reduce((acumulador, item) => acumulador + Number(item.precio),0);
            // esta fucion acumula todos los valores numericos que exista en el arreglo
        }
    },
    methods:{
        removerItem(item){
            this.$emit('remover-item', item);
        }
    } 
    
}
</script>


<style>

</style>