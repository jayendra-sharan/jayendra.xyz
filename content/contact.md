+++
title = 'Contact'
+++

# Say Hello 👋

---

<form id="contact-form">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>

<label for="email">Your Email:</label>
<input type="email" id="email" name="email" required>

<label for="subject">Subject:</label>
<input type="text" id="subject" name="subject" required>

<label for="message">Your Message:</label>
<textarea id="message" name="message" rows="5" required></textarea>

<button id='submit-button' type="submit">Send Message</button>

</form>

<p id="response-message"></p>

<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>

<script>
  (function() {
      var submitButton = document.getElementById('submit-button');
      emailjs.init({
          publicKey: 'dzoZYfbpAIQVxcSAU'
        });
      document.getElementById("contact-form").addEventListener("submit", function(event) {
          event.preventDefault();
          submitButton.disabled = true;
          emailjs.send("service_iflzea9", "template_bbzk4gc", {
              name: document.getElementById("name").value,
              email: document.getElementById("email").value,
              subject: document.getElementById("subject").value,
              message: document.getElementById("message").value
          })
          .then(function(response) {
              document.getElementById("response-message").innerHTML = "Message sent successfully!";
              document.getElementById("contact-form").reset();
              submitButton.disabled = false;
          }, function(error) {
              submitButton.disabled = false;
              document.getElementById("response-message").innerHTML = "Failed to send message. Try again.";
          });
      });
  })();
</script>
