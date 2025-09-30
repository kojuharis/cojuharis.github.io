---
layout: default
title: Archive
permalink: /archive/
---

<div class="post">
    <header class="post-header">
        <h1 class="post-title">Post Archive</h1>
    </header>
    
    <div class="post-content">
        {% if site.posts.size > 0 %}
            <p>All {{ site.posts.size }} post{% if site.posts.size != 1 %}s{% endif %} in chronological order:</p>
            
            {% for post in site.posts %}
                {% assign current_year = post.date | date: "%Y" %}
                {% assign previous_year = post.previous.date | date: "%Y" %}
                
                {% if current_year != previous_year %}
                    <h2>{{ current_year }}</h2>
                {% endif %}
                
                <div class="archive-post">
                    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d" }}</time>
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                </div>
            {% endfor %}
        {% else %}
            <p>No posts yet! Check back soon for new content.</p>
        {% endif %}
    </div>
</div>

<style>
.archive-post {
    display: flex;
    align-items: baseline;
    margin-bottom: 0.5rem;
    padding: 0.5rem 0;
    border-bottom: 1px solid #f1f3f4;
}

.archive-post time {
    color: #666;
    font-size: 0.9rem;
    min-width: 120px;
    margin-right: 1rem;
}

.archive-post a {
    color: #2a7ae4;
    text-decoration: none;
    flex: 1;
}

.archive-post a:hover {
    text-decoration: underline;
}

.archive-post:last-child {
    border-bottom: none;
}
</style>