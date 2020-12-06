<template>
    <div class="card text-white bg-dark">
                <div class="d-flex justify-content-center p-2">
                    <img v-bind:src="(member.image)" alt="Fotografia equipo" >
                </div>
                <div class="card-body">
                    <h5 class="card-title">{{member.nombre}}</h5>
                    <h6 class="card-text"><span>Código:</span>{{member.codigo}}</h6> 
                    <h6 class="card-text"><span> Rol:</span> {{member.rol}}</h6>
                    <p class="card-text">- {{member.descripcion}}</p>
                </div>
                
            </div>
</template>

<script>
    export default {
        name: "TeamCard",
        props: ['member']
    }
</script>

<style scoped>

</style>
