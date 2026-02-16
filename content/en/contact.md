---
title: "Contact"
description: "Get in touch"
---

## Get in Touch

Have a question, idea, or just want to say hello? Send me a message using the form below.

<form action="https://formspree.io/f/xnjbdogb" method="POST" class="contact-form">
  <label for="name">Name</label>
  <input type="text" id="name" name="name" required placeholder="Your name">

  <label for="email">Email</label>
  <input type="email" id="email" name="email" required placeholder="your@email.com">

  <label for="message">Message</label>
  <textarea id="message" name="message" rows="6" required placeholder="What's on your mind?"></textarea>

  <input type="text" name="_gotcha" style="display:none">

  <button type="submit" class="button">Send Message</button>
</form>

<style>
.contact-form {
  max-width: 600px;
}
.contact-form label {
  display: block;
  margin-top: 20px;
  margin-bottom: 6px;
  font-family: var(--rounded-font-family);
  font-weight: 600;
  font-size: 14px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  color: var(--gray-800);
}
.contact-form input[type="text"],
.contact-form input[type="email"],
.contact-form textarea {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid var(--gray-300);
  border-radius: 6px;
  font-family: var(--rounded-font-family);
  font-size: 16px;
  color: var(--text-color);
  background: var(--white);
  transition: border-color 0.2s;
  box-sizing: border-box;
}
.contact-form input[type="text"]:focus,
.contact-form input[type="email"]:focus,
.contact-form textarea:focus {
  outline: none;
  border-color: var(--primary-700);
}
.contact-form textarea {
  resize: vertical;
}
.contact-form .button {
  margin-top: 24px;
  cursor: pointer;
  border: none;
  font-family: var(--condensed-font-family);
  font-size: 16px;
}
</style>
