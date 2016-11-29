<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <link rel="stylesheet" type="text/css" href="../node_modules/bootstrap/dist/css/bootstrap.css">
</head>
<body>
<div class="container">
    <div class="col-md-6 col-md-offset-3"><h1>Vue demo</h1>
        <div id="app">
            <a v-bind:href="url">1</a>
            <a v-on:click="doSomething">2</a>
        </div>
    </div>
</div>




<script src="../node_modules/vue/dist/vue.js"></script>
<script>
    new Vue({
        data: {
            url:'a.html'
        },

    })
</script>
</body>
</html>
