---
layout: home
---

<div class="index-content project">
    <div class="section">
        <ul class="artical-cate">
            <li style="text-align:left"><a href="/"><span>我的博客</span></a></li>
            <li class="on" style="text-align:center"><a href="/project"><span>项目</span></a></li>
            <li style="text-align:right"><a href="/opinion"><span>观点</span></a></li>
        </ul>

        <div class="cate-bar"><span id="cateBar"></span></div>

        <ul class="artical-list">
        {% for post in site.categories.project %}
            <li>
                <h2>
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>
    </div>
    <div class="aside">
    </div>
</div>
