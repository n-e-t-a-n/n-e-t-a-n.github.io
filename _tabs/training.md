---
title: Recit Trainer
icon: fas fa-user-graduate
order: 6
---

<div class="trainer-list">
  {% for trainer in site.trainers %}
    <div class="trainer-item">
      <h2 class="trainer-title">
        <a href="{{ trainer.url }}">{{ trainer.title }}</a>
      </h2>
      {% if trainer.excerpt %}
        <p class="trainer-excerpt">{{ trainer.excerpt | strip_html | truncate: 160 }}</p>
      {% endif %}
    </div>
  {% endfor %}
</div>

<style>
.trainer-list {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-top: 1.5rem;
}

.trainer-item {
  border-left: 3px solid var(--link-color);
  padding-left: 1rem;
}

.trainer-title {
  font-size: 1.1rem;
  margin: 0 0 0.25rem 0;
}

.trainer-title a {
  color: var(--text-color);
  text-decoration: none;
  font-weight: 600;
}

.trainer-excerpt {
  margin: 0;
  font-size: 0.9rem;
  color: var(--text-muted-color);
}
</style>
