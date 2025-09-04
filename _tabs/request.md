---
layout: page
title: "Request a Digest"
icon: fas fa-link
order: 5
---

Use this form to submit a link from **lawphil.net** only.  

<form id="urlForm">
  <label for="urlInput">Enter URL:</label><br>
  <input type="url" id="urlInput" name="url" placeholder="https://lawphil.net/..." required style="width: 100%; padding: 0.5em;"><br><br>
  <button type="submit" style="font-weight:500;padding:0.5rem 1.2rem;border:none;border-radius:0.375rem;cursor:pointer;box-shadow:0 2px 4px rgba(0,0,0,0.1);transition:0.2s;color:#fff;background-color:#7d7d7d;">Submit</button><style>@media (prefers-color-scheme: dark){button{background-color:#e5e7eb;color:#111827;}}</style>

</form>

<div id="response" style="margin-top: 1em;"></div>

<script>
document.getElementById('urlForm').addEventListener('submit', async (e) => {
  e.preventDefault();

  const urlInput = document.getElementById('urlInput').value.trim();
  const responseDiv = document.getElementById('response');
  responseDiv.innerHTML = "";

  let url;
  try {
    url = new URL(urlInput);
  } catch (err) {
    responseDiv.innerHTML = `<span style="color: red;">Please enter a valid URL.</span>`;
    return;
  }

  if (url.hostname !== "lawphil.net") {
    responseDiv.innerHTML = `<span style="color: red;">Only URLs from lawphil.net are accepted.</span>`;
    return;
  }

  responseDiv.innerHTML = "Processing your request... You can leave this page and come back later.";

  try {
    const res = await fetch('https://lawdigestrequests.onrender.com/digest', { 
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ url: url.href })
    });

    const data = await res.json();

    if (!res.ok) {
      responseDiv.innerHTML = `<span style="color:rgb(235, 130, 130);">${data.error}</span>`;
      return;
    }

    responseDiv.innerHTML = `
      <span style="color:rgb(165, 244, 176);">The digest has been successfully created.</span>
    `;
  } catch (err) {
    responseDiv.innerHTML = `<span style="color:rgb(235, 130, 130);">${err.message}</span>`;
  }
});
</script>

