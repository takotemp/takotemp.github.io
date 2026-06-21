<template>
    <div class="page">
        <header class="header">
            <h1>TakoTemp's Log</h1>
            <nav>
                <a href="">首页</a>
                <a href="">文章</a>
                <a href="">关于</a>
            </nav>
        </header>
        <main class="main">
            <article class="post">

                <h2>第一篇博客</h2>
                <p class="time">2026.6.21</p>
                <p>ok啊,也是写上了</p>

            </article>
            <article class="post">

                <h2>第二篇博客</h2>
                <p class="time">2026.6.21</p>
                <p>ok啊,也是写上了第二个了</p>

            </article>
        </main>
        <footer class="footer">版权声明:啥也没有</footer>
    </div>
</template>

<script setup>
</script>

<style scoped>

.page {
    max-width: 600px;
    margin: 0 auto;
    padding: 40px 20px;
    font-family: sans-serif;
    color: #444;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    border-bottom: 1px solid #eee;
    padding-bottom: 16px;
    margin-bottom: 40px;
}

nav a {
    margin-left: 25px;
    text-decoration: none;
    color: #999;
    font-size: 14px;
}

nav a:hover {
    color: #444;
}

.top{
    min-height: 400px;
}

.post {
    margin-bottom: 36px;
}

.post h2 {
    margin: 0 0 6px 0;
    color: #333;
}

.time {
    font-size: 13px;
    color: #bbb;
    margin: 0 0 10px 0;
}

.post p:last-of-type {
    font-size: 15px;
    line-height: 1.8;
    color: #555;
    margin: 0;
}

.footer {
    border-top: 1px soild #eee;
    padding-top: 16px;
    text-align: center;
    font-size: 13px;
    color: #bbb;
}

.main {
    flex: 1;
}
</style>
