---
layout: page
title: Contact Me
permalink: /talk/
---

Looking Forward to answering your message.

---

<form action="//formspree.io/email@domain.com" method="POST" >
    <fieldset style="background-color:#29A7E6">
        <label for="name">Your name</label><br>
        <input type="text" name="name" placeholder="Name" required>
    </fieldset>
    <fieldset style="background-color:#29A7E6">
        <label for="_replyto">Your email</label><br>
        <input type="email" name="_replyto" placeholder="example@domain.com" required>
    </fieldset>
    <fieldset style="background-color:#29A7E6">
        <label for="message">Your message</label><br>
        <textarea name="message" rows="2" placeholder="Message" required></textarea>
    </fieldset>
    <input class="hidden" type="text" name="_gotcha" style="display:none">
    <input class="hidden" type="hidden" name="_subject" value="Message via http://domain.com">

    <input class="button submit" type="submit" value="Send">
</form>
