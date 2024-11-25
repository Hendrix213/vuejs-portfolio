<template>
  <div class="contact-page">
    <!-- Back Button -->
    <button @click="goBack" class="back-btn">Back to Profile</button>

    <!-- Page Title -->
    <h1>Contact Me</h1>

    <!-- Contact Form -->
    <form @submit.prevent="submitForm" class="contact-form">
      <div class="form-group">
        <label for="name">Your Name</label>
        <input type="text" id="name" v-model="form.name" placeholder="Enter your name" required />
      </div>

      <div class="form-group">
        <label for="email">Your Email</label>
        <input type="email" id="email" v-model="form.email" placeholder="Enter your email" required />
      </div>

      <div class="form-group">
        <label for="message">Your Message</label>
        <textarea id="message" v-model="form.message" placeholder="Type your message here" required></textarea>
      </div>

      <button type="submit" class="submit-btn">Send Message</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: '',
      },
    };
  },
  methods: {
    submitForm() {
      alert('Message Sent!');
      this.form = { name: '', email: '', message: '' };
    },
    goBack() {
      this.$router.push('/portfolio/profile'); // Navigate back to the profile page
    },
  },
};
</script>

<style scoped>
/* Contact Page Container */
.contact-page {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  max-width: 600px;
  margin: 50px auto;
  padding: 40px;
  background: linear-gradient(to right, #6a11cb, #2575fc);
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  color: white;
  text-align: center;
}

/* Title Styling */
.contact-page h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
  color: white;
  font-weight: 700;
}

/* Back Button */
.back-btn {
  position: absolute;
  top: 20px;
  left: 20px;
  background-color: #fff;
  color: #333;
  padding: 12px 20px;
  border: none;
  border-radius: 30px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.back-btn:hover {
  background-color: #f1f1f1;
  transform: scale(1.05);
}

/* Form Styling */
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* Form Group */
.form-group {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 100%;
}

label {
  font-size: 1rem;
  color: #f1f1f1;
  margin-bottom: 8px;
  font-weight: 600;
}

/* Input and Textarea Styling */
input,
textarea {
  width: 100%;
  padding: 14px;
  font-size: 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #fff;
  color: #333;
  box-sizing: border-box;
  transition: border 0.3s ease, box-shadow 0.3s ease;
}

input:focus,
textarea:focus {
  border: 1px solid #3498db;
  box-shadow: 0 0 8px rgba(52, 152, 219, 0.4);
  outline: none;
}

/* Submit Button */
.submit-btn {
  background-color: #3498db;
  color: white;
  padding: 14px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1.2rem;
  font-weight: 600;
  text-transform: uppercase;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.submit-btn:hover {
  background-color: #2980b9;
  transform: translateY(-3px);
}

.submit-btn:active {
  transform: translateY(1px);
}

/* Responsive Design */
@media (max-width: 768px) {
  .contact-page {
    padding: 20px;
  }

  .back-btn {
    top: 10px;
    left: 10px;
    padding: 10px 18px;
  }

  .submit-btn {
    font-size: 1rem;
    padding: 12px 18px;
  }
}
</style>
