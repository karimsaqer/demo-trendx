<template>
  <section id="contact" class="contact">
    <div class="container">
      <div class="section-header">
        <h2>Get In Touch</h2>
        <p
          >Have questions about our trips? We're here to help you plan your
          perfect adventure</p
        >
      </div>

      <div class="contact-wrapper">
        <div class="contact-info">
          <div class="info-card">
            <div class="info-icon">
              <svg
                width="24"
                height="24"
                fill="currentColor"
                viewBox="0 0 16 16">
                <path
                  d="M3.654 1.328a.678.678 0 0 0-1.015-.063L1.605 2.3c-.483.484-.661 1.169-.45 1.77a17.568 17.568 0 0 0 4.168 6.608 17.569 17.569 0 0 0 6.608 4.168c.601.211 1.286.033 1.77-.45l1.034-1.034a.678.678 0 0 0-.063-1.015l-2.307-1.794a.678.678 0 0 0-.58-.122l-2.19.547a1.745 1.745 0 0 1-1.657-.459L5.482 8.062a1.745 1.745 0 0 1-.46-1.657l.548-2.19a.678.678 0 0 0-.122-.58L3.654 1.328zM1.884.511a1.745 1.745 0 0 1 2.612.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z" />
              </svg>
            </div>
            <div class="info-content">
              <h3>Phone</h3>
              <p>+20 (123) 123-4567-89</p>
            </div>
          </div>

          <div class="info-card">
            <div class="info-icon">
              <svg
                width="24"
                height="24"
                fill="currentColor"
                viewBox="0 0 16 16">
                <path
                  d="M.05 3.555A2 2 0 0 1 2 2h12a2 2 0 0 1 1.95 1.555L8 8.414.05 3.555zM0 4.697v7.104l5.803-3.558L0 4.697zM6.761 8.83l-6.57 4.027A2 2 0 0 0 2 14h12a2 2 0 0 0 1.808-1.144l-6.57-4.027L8 9.586l-1.239-.757zm3.436-.586L16 11.801V4.697l-5.803 3.546z" />
              </svg>
            </div>
            <div class="info-content">
              <h3>Email</h3>
              <p>demo@demo.com</p>
            </div>
          </div>

          <div class="info-card">
            <div class="info-icon">
              <svg
                width="24"
                height="24"
                fill="currentColor"
                viewBox="0 0 16 16">
                <path
                  d="M8 16s6-5.686 6-10A6 6 0 0 0 2 6c0 4.314 6 10 6 10zm0-7a3 3 0 1 1 0-6 3 3 0 0 1 0 6z" />
              </svg>
            </div>
            <div class="info-content">
              <h3>Address</h3>
              <p>123 Alexandria</p>
            </div>
          </div>
        </div>

        <div class="contact-form">
          <form @submit.prevent="handleSubmit">
            <div class="form-row">
              <div class="form-group">
                <label>Your Name</label>
                <input
                  type="text"
                  v-model="name"
                  placeholder="John Doe"
                  required />
              </div>
              <div class="form-group">
                <label>Email Address</label>
                <input
                  type="email"
                  v-model="email"
                  placeholder="john@example.com"
                  required />
              </div>
            </div>

            <div class="form-group">
              <label>Phone Number</label>
              <input
                type="tel"
                v-model="phone"
                placeholder="+20 (111) 123-4567-89"
                required />
            </div>

            <div class="form-group">
              <label>Your Message</label>
              <textarea
                v-model="message"
                placeholder="Tell us about your travel plans..."
                rows="5"
                required></textarea>
            </div>

            <button type="submit" class="submit-btn">
              <svg
                width="20"
                height="20"
                fill="currentColor"
                viewBox="0 0 16 16">
                <path
                  d="M15.854.146a.5.5 0 0 1 .11.54l-5.819 14.547a.75.75 0 0 1-1.329.124l-3.178-4.995L.643 7.184a.75.75 0 0 1 .124-1.33L15.314.037a.5.5 0 0 1 .54.11ZM6.636 10.07l2.761 4.338L14.13 2.576 6.636 10.07Zm6.787-8.201L1.591 6.602l4.339 2.76 7.494-7.493Z" />
              </svg>
              Send Message
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactUs",
  data() {
    return {
        // just for erase after sending
        name: "",
        email: "",
        phone: "",
        message: "",
    };
  },
  methods: {
    handleSubmit() {
      alert("Thank you for your message! We will get back to you soon.");
      this.name = "";
      this.email = "";
      this.phone = "";
      this.message = "";
    },
  },
};
</script>

<style scoped>
.contact {
  padding: 80px 0;
  background: var(--gray-bg);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.section-header h2 {
  font-size: 36px;
  color: var(--text-dark);
  margin-bottom: 12px;
}

.section-header p {
  font-size: 16px;
  color: var(--text-light);
}

.contact-wrapper {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 60px;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.info-card {
  background: var(--white);
  padding: 24px;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.08);
  display: flex;
  gap: 20px;
  align-items: flex-start;
  transition: all 0.4s ease;
}

.info-card:hover {
  transform: translateY(-8px) scale(1.05);
  box-shadow: 0 8px 20px rgba(254, 175, 12, 0.4);
  border: 1px solid var(--secondary-color);
}

.info-card:hover .info-icon {
  background: linear-gradient(135deg, #ffd54f 0%, var(--secondary-color) 100%);
  color: white;
  transform: rotate(360deg) scale(1.1);
}

.info-icon {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--primary-color);
}

.info-content h3 {
  font-size: 18px;
  color: var(--text-dark);
  margin-bottom: 6px;
}

.info-content p {
  font-size: 14px;
  color: var(--text-light);
}

.contact-form {
  background: var(--white);
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  margin-bottom: 24px;
}

.form-group label {
  display: block;
  font-size: 14px;
  font-weight: 600;
  color: var(--text-dark);
  margin-bottom: 8px;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 14px 16px;
  border: 1px solid var(--primary-color);
  border-radius: 8px;
  font-size: 15px;
  font-family: inherit;
  transition: border-color 0.3s;
  outline: none;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: var(--primary-color);
}

.submit-btn {
  width: 100%;
  background: var(--primary-color);
  color: var(--white);
  padding: 16px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  transition: background 0.3s, transform 0.2s;
}

.submit-btn:hover {
  transform: translateY(-5px);
}

@media (max-width: 968px) {
  .contact-wrapper {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .form-row {
    grid-template-columns: 1fr;
  }
}
</style>
