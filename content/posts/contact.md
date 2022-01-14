---
title: Contact
date: 2020-07-14
description: Contact page.
slug: contact
tags:
- about
menu:
  main:
    weight: 5

---
{{< lead >}}
Drop me a line.
{{< /lead >}}

<style>
fieldset {
	border: medium none !important;
	margin: 0 0 10px;
	min-width: 100%;
	padding: 0;
	width: 100%;
}
#contact input[type="text"], #contact input[type="email"], #contact input[type="tel"], #contact input[type="url"], #contact textarea {
	width:100%;
    color: #000;
	border:1px solid #CCC;
	background:#FFF;
	margin:0 0 5px;
	padding:10px;
}
#contact textarea {
	height:100px;
	max-width:100%;
    resize:none;
}
#contact input:focus, #contact textarea:focus {
	outline:0;
	border:1px solid #999;
}
</style>
  <form id="contact" name="0x40-me-contact-form" method="POST" data-netlify="true" netlify-honeypot="bot-field">
    <p class="hidden">
        <label>Don’t fill this out if you’re human: <input name="bot-field" /></label>
    </p>
    <fieldset>
      <input placeholder="Your name" type="text" name="name" tabindex="1" required autofocus/>
    </fieldset>
    <fieldset>
      <input placeholder="Your Email Address" type="email" name="email" tabindex="2" required autofocus/>
    </fieldset>
    <fieldset>
      <textarea placeholder="Type your Message Here...." tabindex="5" type="message" name="message" required></textarea>
    </fieldset>
    <fieldset>
      <button name="submit" type="submit" id="contact-submit">
        {{< button >}}
        Submit
        {{< /button >}}
      </button>
    </fieldset>
  </form>