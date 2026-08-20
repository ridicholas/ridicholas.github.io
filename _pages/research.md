---
title: "Research"
layout: gridlay
sitemap: false
permalink: /Research
---

### Working Papers

<div class="publications">
  <ul class="bibliography" style="list-style-type: none; padding: 0;">

  {% for pub in site.data.publist.working %}
    <li>
      <div class="pub-row" style="display: flex; align-items: flex-start; margin-bottom: 20px;">
        <!-- Publication Image -->
        <div class="col-sm-3 abbr" style="padding-right: 15px; padding-left: 15px; max-width: 350px;">
          {% if pub.image %}
            <img src="{{ pub.image }}" alt="{{ pub.title }}" style="width:100%; max-width:350px;">
          {% endif %}
        </div>

        <!-- Publication Info -->
        <div class="col-sm-9" style="padding-right: 15px; padding-left: 20px;">
          <div class="title">
            <a href="{{ pub.doi }}" target="_blank">{{ pub.title }}</a>
          </div>
          <div class="author" style="font-size: 0.9em;">
            {{ pub.authors | join: ', ' }}
          </div>
          <div class="periodical" style="font-size: 0.85em; color: gray;">
            <em>{{ pub.display }}</em>
          </div>
        </div>


        <!-- Add Code and BibTeX Buttons If Available -->
        <div class="pub-buttons" style="margin-top: 10px;">
          {% if pub.url %}
            <a href="{{ pub.url }}" class="btn btn-outline-dark btn-sm" target="_blank" style="margin-right: 5px;">Code</a>
          {% endif %}
          {% if pub.bibtex %}
            <a href="#" class="btn btn-outline-dark btn-sm bibtex-button" data-bibtex="{{ pub.bibtex | xml_escape }}" onclick="copyBibtex(event)">BibTeX</a>
          {% endif %}

        </div>
      </div>
    </li>
    <br>
  {% endfor %}

  </ul>
</div>

\* denotes first and joint-first author publications

### Publications & In Proceedings

<div class="publications">
  <ul class="bibliography" style="list-style-type: none; padding: 0;">

  {% for pub in site.data.publist.published %}
    <li>
      <div class="pub-row" style="display: flex; align-items: flex-start; margin-bottom: 20px;">
        <!-- Publication Image -->
        <div class="col-sm-3 abbr" style="padding-right: 15px; padding-left: 15px; max-width: 350px;">
          {% if pub.image %}
            <img src="{{ pub.image }}" alt="{{ pub.title }}" style="width:100%; max-width:350px;">
          {% endif %}
        </div>

        <!-- Publication Info -->
        <div class="col-sm-9" style="padding-right: 15px; padding-left: 20px;">
          <div class="title">
            <a href="{{ pub.doi }}" target="_blank">{{ pub.title }}</a>
          </div>
          <div class="author" style="font-size: 0.9em;">
            {{ pub.authors | join: ', ' }}
          </div>
          <div class="periodical" style="font-size: 0.85em; color: gray;">
            <em>{{ pub.display }}</em>
          </div>
        </div>


        <!-- Add Code and BibTeX Buttons If Available -->
        <div class="pub-buttons" style="margin-top: 10px;">
          {% if pub.url %}
            <a href="{{ pub.url }}" class="btn btn-outline-dark btn-sm" target="_blank" style="margin-right: 5px;">Code</a>
          {% endif %}
          {% if pub.bibtex %}
            <a href="#" class="btn btn-outline-dark btn-sm bibtex-button" data-bibtex="{{ pub.bibtex | xml_escape }}" onclick="copyBibtex(event)">BibTeX</a>
          {% endif %}

        </div>
      </div>
    </li>
    <br>
  {% endfor %}

  </ul>
</div>

\* denotes first and joint-first author publications


<script>
function copyBibtex(event) {
  event.preventDefault(); // Prevent the default link behavior

  // Get the BibTeX text from the data attribute
  var bibtex = event.currentTarget.getAttribute('data-bibtex');

  // Use the Clipboard API to copy text
  if (navigator.clipboard && window.isSecureContext) {
    // Navigator clipboard api method'
    navigator.clipboard.writeText(bibtex).then(function() {
      alert('BibTeX entry copied to clipboard!');
    }, function(err) {
      console.error('Could not copy text: ', err);
    });
  } else {
    // Textarea method for older browsers
    var textarea = document.createElement('textarea');
    textarea.value = bibtex;
    // Move textarea out of viewport so it's not visible
    textarea.style.position = 'fixed';
    textarea.style.left = '-999999px';
    textarea.style.top = '-999999px';
    document.body.appendChild(textarea);
    textarea.focus();
    textarea.select();
    try {
      document.execCommand('copy');
      alert('BibTeX entry copied to clipboard!');
    } catch (err) {
      console.error('Could not copy text: ', err);
    }
    document.body.removeChild(textarea);
  }
}
</script>



