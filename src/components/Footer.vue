<template>

    <footer class="footer">
            <div class="container-fluid">
                <div class="row text-muted">
                    <div class="col-12 text-center">
                        <p class="mb-0">
                            <span>&copy; Strategy - {{date}}</span>
                        </p>
                    </div>
                </div>
            </div>
    </footer>

</template>

<script>

export default{
    name:"Footer",
    props:{
       date: String
    }
   
}

</script>

<style scoped>

.footer{
    height: 100px;
    background-color: #d9d9d9;
    border-top: 2px solid #e6e6e6;
    color: #404040;
    display: flex;
    align-items: center;
    justify-content: center;
    bottom: 0;
    width: 100%;
    margin-bottom: 0px;
    position: absolute;
}

</style>
