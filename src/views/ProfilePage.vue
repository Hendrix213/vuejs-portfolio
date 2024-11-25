<template>
  <div class="profile-page">
    <div class="profile-header">
      <!-- Profile Photo -->
      <img :src="profile.photo" alt="Profile Photo" class="profile-photo" />
      <h1>{{ profile.name }}</h1>
      <p class="bio">{{ profile.bio }}</p>
    </div>

    <!-- Social Media Links -->
    <div class="social-links">
      <a
        v-for="(link, platform) in profile.socialMediaLinks"
        :key="platform"
        :href="link"
        :title="platform"
        target="_blank"
        class="social-link"
      >
        <img :src="getIcon(platform)" :alt="platform" class="social-icon" />
      </a>
    </div>

    <!-- Navigation Buttons -->
    <div class="navigation-buttons">
      <button @click="navigateTo('creative')" class="nav-btn">My Creativity</button>
      <button @click="navigateTo('contact')" class="nav-btn">Contact Me</button>
      <button @click="navigateTo('showcase')" class="nav-btn">My Showcase</button>
    </div>

    <!-- Logout Button -->
    <div class="logout-btn-container">
      <button @click="logout" class="logout-btn">Logout</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      profile: {
        name: 'Allen Hendrix Justimbaste',
        photo: require('/public/hendrix.jpg'),
        bio: `"Hello! My name is Allen Hendrix, and I'm a very enthusiastic gym attendee and serious guitar player. I always put in my heart in whatever I am doing, whether it's lifting weights or playing the guitar. For me, fitness breeds discipline and determination, while music fuels the creativity and soul. My goal is to keep pushing myself, inspiring others, and finding harmony in strength and melody."`,
        socialMediaLinks: {
          Facebook: 'https://www.facebook.com/HeneralDrixility',
          GitHub: 'https://github.com/Hendrix213',
        },
      },
    };
  },
  methods: {
    getIcon(platform) {
      switch (platform) {
        case 'Facebook':
          return require('/public/fb.png');
        case 'GitHub':
          return 'https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg';
        default:
          return '';
      }
    },
    navigateTo(page) {
      this.$router.push(`/portfolio/${page}`);
    },
    logout() {
      // You can clear any authentication tokens here if necessary
      // For now, we just redirect to the login page
      this.$router.push('/login');
    },
  },
};
</script>

<style scoped>
/* Overall Page Layout */
.profile-page {
  background: #1e3a8a; /* Blue background */
  text-align: center;
  max-width: 1000px;
  margin: 60px auto;
  padding: 40px;
  border-radius: 20px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  font-family: 'Poppins', sans-serif;
}

/* Profile Header */
.profile-header {
  margin-bottom: 40px;
}

.profile-photo {
  width: 170px;
  height: 170px;
  border-radius: 50%;
  border: 5px solid #4caf50;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.profile-photo:hover {
  transform: scale(1.1);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
}

h1 {
  font-size: 2.6rem;
  font-weight: bold;
  color: #fff; /* White text */
  margin-top: 15px;
}

.bio {
  font-size: 1.2rem;
  color: #e0e0e0; /* Light gray text */
  margin: 15px auto;
  line-height: 1.8;
  max-width: 600px;
  text-align: justify;
}

/* Social Media Icons */
.social-links {
  display: flex;
  justify-content: center;
  gap: 30px;
  margin: 30px 0;
}

.social-icon {
  width: 50px;
  height: 50px;
  border-radius: 10px;
  transition: transform 0.3s ease, background-color 0.3s ease;
}

.social-icon:hover {
  transform: scale(1.15);
}

/* Navigation Buttons */
.navigation-buttons {
  margin-top: 40px;
  display: flex;
  justify-content: center;
  gap: 20px;
}

.nav-btn {
  background: linear-gradient(to right, #4caf50, #2e7d32);
  color: white;
  padding: 12px 30px;
  border: none;
  border-radius: 25px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.nav-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.nav-btn:active {
  transform: scale(0.98);
  box-shadow: none;
}

/* Logout Button */
.logout-btn-container {
  margin-top: 40px;
}

.logout-btn {
  background-color: #f44336;
  color: white;
  padding: 12px 30px;
  border: none;
  border-radius: 25px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.logout-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.logout-btn:active {
  transform: scale(0.98);
  box-shadow: none;
}

/* Responsive Design */
@media (max-width: 768px) {
  .profile-page {
    padding: 20px;
  }

  .bio {
    font-size: 1rem;
  }

  .social-links {
    gap: 20px;
  }

  .nav-btn {
    padding: 10px 20px;
    font-size: 14px;
  }

  .logout-btn {
    padding: 10px 20px;
    font-size: 14px;
  }
}
</style>
