<template>
    <div>
         <Header /> <!-- custom component -->
         <slot />  <!-- page akan mengisi pada bagian ini -->
         <Footer />
</div>
</template>
<style>
.container-fluid{
    background-color:#FFFF ;
    
}

a {
    color: #313131;
    text-decoration: none;
    font-weight: bold;
}
a:hover {
    color: inherit;
}
</style>
