<template>
  <div>
    <!-- Icons and Search Bar Container -->
    <div class="icon-search-container">
      <!-- List Icon -->
      <font-awesome-icon
          class="list-icon"
          icon="list"
          @click="showList"
      />

      <!-- Card Icon -->
      <font-awesome-icon
          class="card-icon"
          icon="th"
          @click="showCard"
      />

      <!-- Search Bar -->
      <input
          type="text"
          v-model="searchTerm"
          @input="filterItems"
          placeholder="Search..."
          class="search-bar"
      />
    </div>

    <!-- Display Filtered Items as Horizontal Cards -->
    <div class="horizontal-card-container">
      <div v-for="item in filteredItems" :key="item.id" class="horizontal-card">
        <!-- Card Image (Replace 'item.image' with your data) -->
        <img :src="item.image" alt="Card Image" class="card-image" />

        <!-- Card Content -->
        <div class="card-content">
          <h3>{{ item.name }}</h3>
          <p>{{ item.details }}</p>
        </div>
      </div>
    </div>

    <div class="card-container">
      <div v-for="item in filteredItems" :key="item.id" class="card">
        <!-- Card Image (Replace 'item.image' with your data) -->
        <img :src="item.image" alt="Card Image" class="card-image" />

        <!-- Card Content -->
        <div class="card-content">
          <h3>{{ item.name }}</h3>
          <p>{{ item.details }}</p>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchTerm: '',
      activeView: 'list', // 'list' or 'card'
      items: [
        { id: 1, name: 'Item 1', image: 'item1.jpg', details: 'Details for Item 1' },
        { id: 2, name: 'Item 2', image: 'item2.jpg', details: 'Details for Item 2' },
        // Add more items
      ],
    };
  },
  computed: {
    filteredItems() {
      const regex = new RegExp(this.searchTerm, 'i');
      return this.items.filter(item => regex.test(item.name));
    },
  },
  methods: {
    showList() {
      this.activeView = 'list';
    },
    showCard() {
      this.activeView = 'card';
    },
    filterItems() {
      // Update the displayed items when the search term changes
    },
  },
};
</script>

<style scoped>
.icon-search-container {
  display: flex;
  align-items: center;
  gap: 10px; /* Adjust the gap as needed */
}

.list-icon,
.card-icon {
  font-size: 24px; /* Adjust the icon size as needed */
  cursor: pointer; /* Change cursor to a pointer on hover */
}

.search-bar {
  flex: 1; /* Allow the search bar to expand and take up the available space */
}

.horizontal-card {
  /* Your card styles */
  border: 1px solid #e0e0e0;
  border-radius: 5px;
  width: 300px; /* Adjust the width as needed */
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  margin: 10px; /* Add margin to create space between cards */
}

.card-image {
  max-width: 100%;
  max-height: 150px; /* Adjust the max-height as needed */
  object-fit: cover;
}

.card-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 10px;
  width: 100%;
}

.card-content h3 {
  margin: 0;
}

.card-content p {
  margin: 0;
}
</style>
