<template>
  <app-layout title="Productos">
    <template #header>
      <InertiaLink :href="route('productos.create')" class="btn btn-sm w-100 btn-success">
          Crear nuevo Producto
      </InertiaLink>
    </template>

    <table class="table">
        <thead>
            <tr>
                <th scope="col">ID</th>
                <th scope="col">Descripcion</th>
                <th scope="col">Precio</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in productos" :key="item.id">
                <th scope="row">{{ item.id }}</th>
                <td>{{ item.descripcion }}</td>
                <td>{{ item.precio }}</td>
                <td>
                    <button type="button" class="btn btn-sm" data-bs-toggle="modal"
                     :data-bs-target="'#exampleModal' + item.id">
                        <i class="fa-solid fa-pen-to-square text-success"></i>
                    </button>
                    <FormEditar :producto="item"></FormEditar>
                </td>
                <td>

                </td>
            </tr>
        </tbody>
    </table>

  </app-layout>
</template>

<script>
import FormEditar from './FormEditar.vue'

export default({
    props: {
        'productos' : Array
    }, 
    components: {
        FormEditar
    }
});
</script>
