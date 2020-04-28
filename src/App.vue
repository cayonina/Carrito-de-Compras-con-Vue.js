<template>
  <div id="app">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="prod in productos" :key="prod.id">
            <!-- aqui  en esta directiva como evento le mandaremos los productos por cada prod -->
            <!-- en v-on le damos el evento de agregar carro -->
            <producto :producto="prod" v-on:agregar-carro="agregarProductoCarro" :estaEnCarrito="estaEnCarrito(prod)"></producto>
          </div>
        </div>
      </div>
      <div class="col-md5 my-5">
        <!-- aqui mando al componente carrito el arreglo carrito -->
        <Carrito :items="carrito" v-on:remover-item="removerProducto" v-on:pagar="pagar"></Carrito>
      </div>
    </div> 
  </div>
</template>

<script>

import productos from './productos.json'
import Producto from './components/Producto.vue'
import Carrito from './components/Carrito.vue'

export default {
  name: 'App',
  components: {
    Producto,
    Carrito
  },
  data(){
    return{
      productos,
      carrito:[]
    }
  },
  methods:{
    agregarProductoCarro(producto){
      this.carrito.push(producto);
    },
    estaEnCarrito(producto){
      const item=this.carrito.find(item => item.id === producto.id);
      if(item){
        return true;
      }
      else{
      return false;
      }
    },
    // metodo para eliminar producto a traves del metodo filter que cre otro arreglo son el eliminado es decir carrito sera el carrito sin el producto identificado
    removerProducto(producto){
      this.carrito=this.carrito.filter(item => item.id != producto.id)
    },
    pagar(){
      this.carrito=[];
      alert('¡¡¡ Venta Completada !!!')
    }
  }
}
</script>

<style>

</style>
