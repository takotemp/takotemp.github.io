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
/* ---------- 页面骨架 ---------- */
.page {
    position: relative;
    isolation: isolate; /* 创建层叠上下文，确保背景网格不会跑到 body 后面 */
    max-width: 600px;
    margin: 0 auto;
    padding: 40px 20px;
    font-family: sans-serif;
    color: #444;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    counter-reset: post;
}

/* 背景网格：瑞典网格风格的“纸面” */
.page::before {
    content: "";
    position: fixed;
    inset: 0;
    z-index: -1;
    pointer-events: none;
    background-image:
        linear-gradient(to right, rgba(68, 68, 68, 0.05) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(68, 68, 68, 0.05) 1px, transparent 1px);
    background-size: 48px 48px;
    background-position: center top;
    -webkit-mask-image: radial-gradient(ellipse 75% 65% at 50% 42%, #000 25%, transparent 100%);
            mask-image: radial-gradient(ellipse 75% 65% at 50% 42%, #000 25%, transparent 100%);
}

/* ---------- 顶部 ---------- */
.header {
    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    border-bottom: 1px solid #eee;
    padding-bottom: 16px;
    margin-bottom: 40px;
    animation: fadeUp 0.8s cubic-bezier(0.2, 0.8, 0.2, 1) both;
}

/* 底边强调线：静态宽度保证 reduced-motion 下仍可见，动画从 0 长到 40px */
.header::after {
    content: "";
    position: absolute;
    left: 0;
    bottom: -1px;
    width: 40px;
    height: 2px;
    background: #444;
    animation: growLine 0.9s 0.25s cubic-bezier(0.2, 0.8, 0.2, 1) both;
}

.header h1 {
    margin: 0;
    letter-spacing: -0.01em;
    color: #333;
}

/* 标题前的小方块，缓慢旋转 */
.header h1::before {
    content: "";
    display: inline-block;
    width: 7px;
    height: 7px;
    margin-right: 10px;
    background: #444;
    vertical-align: 2px;
    animation: spin 8s linear infinite;
}

nav a {
    position: relative;
    margin-left: 25px;
    text-decoration: none;
    color: #999;
    font-size: 14px;
    transition: color 0.3s ease;
}

/* 链接下划线：右侧收起，悬停时从左侧滑出 */
nav a::after {
    content: "";
    position: absolute;
    left: 0;
    right: 0;
    bottom: -4px;
    height: 1px;
    background: currentColor;
    transform: scaleX(0);
    transform-origin: right center;
    transition: transform 0.3s cubic-bezier(0.2, 0.8, 0.2, 1);
}

nav a:hover {
    color: #444;
}

nav a:hover::after {
    transform: scaleX(1);
    transform-origin: left center;
}

/* ---------- 主体 ---------- */
.main {
    flex: 1;
}

.post {
    position: relative;
    margin-bottom: 36px;
    padding-left: 34px;
    counter-increment: post;
    animation: fadeUp 0.7s cubic-bezier(0.2, 0.8, 0.2, 1) both;
}

/* 文章较多时可继续按需追加延迟 */
.post:nth-of-type(1) { animation-delay: 0.12s; }
.post:nth-of-type(2) { animation-delay: 0.24s; }

/* 左侧网格序号：decimal-leading-zero 自动生成 01、02…10 */
.post::before {
    content: counter(post, decimal-leading-zero);
    position: absolute;
    left: 0;
    top: 3px;
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 0.1em;
    font-variant-numeric: tabular-nums;
    color: #d5d5d5;
    transition: color 0.3s ease;
}

/* 序号下方延伸出的竖线，悬停时向下生长 */
.post::after {
    content: "";
    position: absolute;
    left: 8px;
    top: 24px;
    bottom: 4px;
    width: 1px;
    background: #eee;
    transform: scaleY(0);
    transform-origin: top;
    transition: transform 0.45s cubic-bezier(0.2, 0.8, 0.2, 1), background 0.3s ease;
}

.post:hover::before {
    color: #444;
}

.post:hover::after {
    transform: scaleY(1);
    background: #d8d8d8;
}

.post h2 {
    margin: 0 0 6px 0;
    color: #333;
    transition: color 0.3s ease, transform 0.3s cubic-bezier(0.2, 0.8, 0.2, 1);
}

.post:hover h2 {
    color: #111;
    transform: translateX(3px);
}

.time {
    font-size: 13px;
    color: #bbb;
    margin: 0 0 10px 0;
    letter-spacing: 0.02em;
    font-variant-numeric: tabular-nums;
    transition: color 0.3s ease;
}

.post:hover .time {
    color: #999;
}

.post p:last-of-type {
    font-size: 15px;
    line-height: 1.8;
    color: #555;
    margin: 0;
}

/* ---------- 底部 ---------- */
.footer {
    position: relative;
    border-top: 1px solid #eee;
    padding-top: 16px;
    text-align: center;
    font-size: 13px;
    color: #bbb;
    animation: fadeUp 0.8s 0.4s cubic-bezier(0.2, 0.8, 0.2, 1) both;
}

.footer::before {
    content: "";
    position: absolute;
    top: -1px;
    left: 50%;
    width: 24px;
    height: 2px;
    background: #444;
    transform: translateX(-50%);
}

/* ---------- 动画 ---------- */
@keyframes fadeUp {
    from { opacity: 0; transform: translateY(14px); }
    to   { opacity: 1; transform: translateY(0); }
}

@keyframes growLine {
    from { width: 0; }
    to   { width: 40px; }
}

@keyframes spin {
    from { transform: rotate(0deg); }
    to   { transform: rotate(360deg); }
}

@media (prefers-reduced-motion: reduce) {
    .header,
    .footer,
    .post {
        animation: none;
    }
    .header::after,
    .header h1::before {
        animation: none;
    }
    nav a::after,
    .post::after,
    .post h2,
    .time {
        transition: none;
    }
    .post:hover h2 {
        transform: none;
    }
}
</style>