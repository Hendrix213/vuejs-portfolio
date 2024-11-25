<template>
  <div class="creative-page">
    <!-- Back Button -->
    <button @click="goBack" class="back-btn">Back to Profile</button>

    <h1 class="title">My Hobbies</h1>
    <div class="hobby-list">
      <div class="hobby-card" v-for="hobby in hobbies" :key="hobby.id">
        <div v-if="Array.isArray(hobby.photo)">
          <!-- Display multiple images for the 4th hobby -->
          <img v-for="(image, index) in hobby.photo" :key="index" :src="image" :alt="hobby.name" class="hobby-image" />
        </div>
        <div v-else>
          <img :src="hobby.photo" :alt="hobby.name" class="hobby-image" />
        </div>
        <h2 class="hobby-name">{{ hobby.name }}</h2>
        <p class="hobby-description">{{ hobby.description }}</p>
      </div>
    </div>

    <!-- Resume Section -->
    <h1 class="title">Resume</h1>
    <div class="resume-section">
      <p class="resume-description">
        I am a passionate and dedicated individual with a strong interest in various creative pursuits. My hobbies, including basketball, going to the gym, playing the guitar, and traveling, reflect my enthusiasm for staying active, being creative, and exploring the world.
      </p>
      <ul class="resume-details">
        <li><strong>Education:</strong> Bachelor's Degree in Computer Engineering</li>
        <li><strong>Skills:</strong> Web Development, Problem Solving, Teamwork, Creativity</li>
        <li><strong>Interests:</strong> Technology, Fitness, Music, Travel</li>
        <li><strong>Goal:</strong> To continuously grow personally and professionally, using my hobbies and skills to inspire others and make a positive impact.</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CreativePage',
  data() {
    return {
      hobbies: [
        {
          id: 1,
          name: 'Basketball',
          photo: require('/public/basketball.jpg'),
          description: 'Love playing basketball because it’s a great way to stay active, challenge yourself, and have fun with friends. The fast-paced nature of the game, combined with teamwork and strategy, offers both mental and physical stimulation, making it an exciting and rewarding experience.',
        },
        {
          id: 2,
          name: 'Gym',
          photo: require('/public/gym.jpg'),
          description: 'Going to the gym really makes my body be in great shape, boosts my self-confidence, and stretches my abilities. It is not just about muscular strength, but it is also about mental toughness, discipline, and living a healthier lifestyle. This is where I discover my focus and drive to be a better person.',
        },
        {
          id: 3,
          name: 'Guitarist',
          photo: require('/public/guitarista.jpg'),
          description: 'Playing the guitar is more than just a hobby for me; it is a way for me to express my creativity and emotional self. The melodies I come up with allow me to wind down while connecting to people, bringing happiness to those around me. Be it strumming my favorite song or practicing new chords, it seems that in its company I need it to find harmony and inspiration.',
        },
        {
          id: 4,
          name: 'Travel',
          photo: [
            require('/public/bebu.jpg'),
            require('/public/bebuu.jpg'),
            require('/public/bebuuu.jpg'),
          ],
          description: 'Traveling with my bebu is a beautiful experience that allows us to explore new places, immerse ourselves in different cultures, and create unforgettable memories together. Each trip brings us closer, giving us the opportunity to grow as individuals and as a couple. From scenic beach vacations to adventurous mountain hikes, every journey is a reminder of the bond we share and the joy of discovering the world together.',
        },
      ],
    };
  },
  methods: {
    goBack() {
      this.$router.push('/portfolio/profile');
    },
  },
};
</script>

<style scoped>
/* Overall Page Layout */
.creative-page {
  text-align: center;
  padding: 40px;
  font-family: 'Roboto', sans-serif;
  background-color: #e0f7fa;
  max-width: 1000px;
  margin: 40px auto;
  border-radius: 12px;
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 2.8rem;
  color: #1a202c;
  font-weight: 700;
  margin-bottom: 40px;
  text-transform: uppercase;
  letter-spacing: 2px;
}

/* Hobby List Styling */
.hobby-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 25px;
}

.hobby-card {
  background: #ffffff;
  border: none;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  text-align: left;
}

.hobby-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 20px rgba(0, 0, 0, 0.15);
}

.hobby-image {
  width: 300px; /* Medium size */
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 15px;
}

.hobby-name {
  font-size: 1.6rem;
  color: #2d3748;
  font-weight: bold;
  margin-bottom: 10px;
}

.hobby-description {
  font-size: 1rem;
  color: #4a5568;
  line-height: 1.5;
}

.back-btn {
  background-color: #3182ce;
  color: white;
  padding: 12px 30px;
  margin-bottom: 30px;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  font-size: 16px;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.back-btn:hover {
  background-color: #2b6cb0;
  transform: scale(1.1);
}

/* Resume Section Styling */
.resume-section {
  text-align: left;
  background: #ffffff;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.08);
  margin-top: 40px;
}

.resume-description {
  font-size: 1.1rem;
  color: #2d3748;
  margin-bottom: 20px;
  line-height: 1.6;
}

.resume-details {
  list-style-type: none;
  padding: 0;
}

.resume-details li {
  font-size: 1rem;
  color: #4a5568;
  margin-bottom: 10px;
}

.resume-details strong {
  color: #1a202c;
}
</style>
