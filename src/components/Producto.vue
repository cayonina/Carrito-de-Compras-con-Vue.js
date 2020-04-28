<template>
    <div class="card my-5">
        <div class="card-body">
            <h5 class="text-center card-title">{{producto.titulo}}</h5>
            <!-- aqui para la imagen es un binding por la imagen asi que se antepone un : -->
            <img :src="producto.imagen" width="290" height="150">
            <!-- se le da formato con ese metodo -->
            <!-- :disabled hace que bloquee el boton en caso que sea verdad el valor que viene en esta en carrito -->
            <p class="text-center text-muted card-text display-4" >$ {{Number(producto.precio).toFixed()}}</p>
            <button @click="agregarCarro(producto)" class="btn btn-primary form-control" :disabled="estaEnCarrito" >
               {{ estaEnCarrito ? 'Agregado' : 'Agregar al Carrito'}}
            </button>
        </div>
    </div>
</template>


<script>
export default {
    name:'Producto',
    // asi se recibe los datos que vengan del padre si es un arreglo
    props: ['producto', 'estaEnCarrito'],
    methods:{
        // el metodo para agregar al carro aqui mandoa el prod. a App.vue
        agregarCarro(producto){
            this.$emit('agregar-carro', producto);
        }
    }    
}
</script>

<style>

</style>