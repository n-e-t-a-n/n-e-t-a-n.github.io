---
title: Rules of Court
icon: fas fa-gavel
order: 5
---

<div class="rules-list">
  {% for rule in site.rules %}
    <div class="rule-item">
      <h2 class="rule-title">
        <a href="{{ rule.url }}">{{ rule.title }}</a>
      </h2>
    </div>
  {% endfor %}
</div>

<style>
.rules-list {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-top: 1.5rem;
}

.rule-item {
  border-left: 3px solid var(--link-color);
  padding-left: 1rem;
}

.rule-title {
  font-size: 1.1rem;
  margin: 0 0 0.25rem 0;
}

.rule-title a {
  color: var(--text-color);
  text-decoration: none;
  font-weight: 600;
}

.rule-excerpt {
  margin: 0;
  font-size: 0.9rem;
  color: var(--text-muted-color);
}
</style>
