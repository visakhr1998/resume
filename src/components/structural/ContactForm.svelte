<script>
    let name = '';
    let email = '';
    let message = '';
  
    const isValidEmail = (email) => {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(email);
    };
  
    const handleSubmit = () => {
      // Add your form submission logic here
      if (isValidEmail(email)) {
        alert(`Form submitted!\nName: ${name}\nEmail: ${email}\nMessage: ${message}`);
      } else {
        alert('Invalid email address. Please provide a valid email.');
      }
    };
  </script>
  
  <style>
    /* Add your styles here */
  </style>
  
  <div class="contact-form">
    <h2>Contact Me</h2>
    <form on:submit|preventDefault={handleSubmit}>
      <label for="name">Name:</label>
      <input type="text" id="name" bind:value={name} required />
  
      <label for="email">Email:</label>
      <input type="email" id="email" bind:value={email} required />
  
      <label for="message">Message:</label>
      <textarea id="message" bind:value={message} required></textarea>
  
      <button type="submit">Submit</button>
    </form>
  </div>
  