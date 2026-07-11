---
title: Home
---
<section class="hero" id="home">
  <p class="eyebrow">data engineering portfolio</p>
  <h1>I turn messy data into pipelines people can trust.</h1>
  <p class="hero__role">Support Specialist &rarr; Data Engineer in progress</p>
  <p class="hero__lede">
    I'm Judith. My background is customer support and community management, my degrees are in chemical
    engineering and business — and I'm now building the SQL, pipeline, and warehouse skills to work as a
    data engineer, fully remote. Everything below is real work: real queries, real datasets, real repos.
  </p>
  <div class="hero__cta">
    <a href="#projects" class="btn">View projects</a>
    <a href="#contact" class="btn btn--ghost">Get in touch</a>
  </div>
</section>

<section id="about">
  <div class="section-head">
    <h2>About</h2>
  </div>
  {% include about-content.html %}
</section>

<section id="skills">
  <div class="section-head">
    <h2>Skills</h2>
  </div>
  {% include skills-content.html %}
</section>

<section id="certifications">
  <div class="section-head">
    <h2>Certifications</h2>
  </div>
  {% include certifications-content.html %}
</section>

<section id="projects">
  <div class="section-head">
    <h2>Projects</h2>
  </div>
  <div class="project-grid">
    {% for project in site.projects %}
    <div class="project-card">
      <h3>{{ project.title }}</h3>
      <p>{{ project.tagline }}</p>
      {% if project.flow %}
      <div class="flow-marker">
        {% assign steps = project.flow | split: "->" %}
        {% for step in steps %}
          <span class="flow-step">{{ step | strip }}</span>
          {% unless forloop.last %}<span class="flow-arrow">&rarr;</span>{% endunless %}
        {% endfor %}
      </div>
      {% endif %}
      {% if project.stack %}
      <ul class="tag-list">
        {% for tool in project.stack %}<li class="tag">{{ tool }}</li>{% endfor %}
      </ul>
      {% endif %}
      <div class="project-links">
        <a href="{{ project.url | relative_url }}">Full write-up &rarr;</a>
        {% if project.repo %}<a href="{{ project.repo | split: ' #' | first }}" target="_blank" rel="noopener">Repo &#8599;</a>{% endif %}
      </div>
    </div>
    {% endfor %}
  </div>
</section>

<section id="blog">
  <div class="section-head">
    <h2>Blog</h2>
    <a href="{{ '/blog/' | relative_url }}" class="view-all">all posts &rarr;</a>
  </div>
  <ul class="post-list">
    {% for post in site.posts limit:3 %}
    <li>
      <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span><br>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
    {% else %}
    <li>No posts yet — add markdown files to <code>docs/_posts/</code> named <code>YYYY-MM-DD-title.md</code>.</li>
    {% endfor %}
  </ul>
</section>

<section id="contact">
  <div class="section-head">
    <h2>Contact</h2>
  </div>
  <p class="hero__lede">Open to remote data analyst / junior data engineer roles — genuinely global, not region-restricted.</p>
  {% include contact-content.html %}
</section>
