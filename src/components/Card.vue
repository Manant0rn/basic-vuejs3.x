<template>
  <li>
    <img src="https://sm.ign.com/ign_nordic/cover/a/avatar-gen/avatar-generations_prsz.jpg" />
    <hr/>
    <!-- Slots -->
    <!-- <slot></slot> -->

    <!-- Named Slots -->
    <slot name="card-header"></slot>
    <slot name="card-button"></slot>
    <slot name="card-content"></slot>
  </li>
</template>

<script>
export default {

}
</script>

<style scoped>
    li{
        margin: 1rem 0;
        font-size: 1.25rem;
        font-weight: bold;
        background: purple;
        padding: 0.5rem;
        color: #fff;
        border-radius: 25px;
    }
    img{
        width: 100px;
        height: 100px;
    }
</style>