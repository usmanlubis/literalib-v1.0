<template>
  <main>
    <div class="py-4">
      <div class="container">
        <div class="title border-bottom d-flex align-items-center justify-content-between py-2">
          <h5>Books</h5>
          <div class="d-flex align-items-center ms-auto">
            <div class="dropdown me-2">
              <button class="btn btn-primary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                {{ category }}
              </button>
              <ul class="dropdown-menu">
                <li><button class="dropdown-item" @click="category = 'All Categories'" >All</button></li>
                <li><button class="dropdown-item" @click="category = 'Productivity'" >Productivity</button></li>
                <li><button class="dropdown-item" @click="category = 'Self-help'" >Self-help</button></li>
                <li><button class="dropdown-item" @click="category = 'Biography'" >Biography</button></li>
                <li><button class="dropdown-item" @click="category = 'Fiction'" >Fiction</button></li>
              </ul>
            </div>
            <div class="d-flex align-items-center justify-content-end w-100">
              <span class="me-2">View As</span>
              <button
                class="btn btn-outline-secondary py-1 px-3"
                @click="isGrid = !isGrid">
                {{ isGrid ? 'Grid' : 'List' }}
              </button>
            </div>
          </div>
        </div>
        <div class="list-book row g-3">
          <CardItem
            v-for="(book, index) in filteredBooks"
            :key="index"
            :book="book"
            :is-grid="isGrid"
          />
        </div>
        <div class="action py-2">
          <a v-if="!isCreating" href="#" class="add-button" @click="isCreating = !isCreating">Add Book</a>
          <div v-else class="add-card">
            <form @submit.prevent="addBook">
              <div class="mb-3">
                <input id="bookTitle" v-model="form.title" type="text" name="bookTitle" class="form-control" placeholder="Book Title" required>
              </div>
              <div class="mb-3">
                <input id="bookPoster" v-model="form.poster" type="text" name="bookPoster" class="form-control" placeholder="Poster URL" required>
              </div>
              <div class="mb-3">
                <textarea id="bookDescription" v-model="form.description" name="bookDescription" class="form-control" rows="3" placeholder="Description" required></textarea>
              </div>
              <p style="margin-bottom: 5px;">Category:</p>
              <div class="form-check">
                <input id="productivity" v-model="form.category" class="form-check-input" type="radio" name="bookCategory" value="Productivity" required>
                <label class="form-check-label" for="productivity">
                  Productivity
                </label>
              </div>
              <div class="form-check">
                <input id="self_help" v-model="form.category" class="form-check-input" type="radio" name="bookCategory" value="Self-help" required>
                <label class="form-check-label" for="self_help">
                  Self-help
                </label>
              </div>
              <div class="form-check">
                <input id="biography" v-model="form.category" class="form-check-input" type="radio" name="bookCategory" value="Biography" required>
                <label class="form-check-label" for="biography">
                  Biography
                </label>
              </div>
              <div class="form-check">
                <input id="fiction" v-model="form.category" class="form-check-input" type="radio" name="bookCategory" value="Fiction" required>
                <label class="form-check-label" for="fiction">
                  Fiction
                </label>
              </div>
              <div class="button-wrapper d-flex mt-3">
                <button class="btn btn-primary me-2" type="submit">Add book</button>
                <button class="btn btn-outline-secondary" @click="isCreating = !isCreating">Cancel</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
  import CardItem from '@/components/Card/CardItem.vue';
  export default {
    name: 'IndexPage',
    components: {
      CardItem
    },
    data() {
      return {
        books: [],
        isCreating: false,
        isGrid: false,
        category: 'All Categories',
        form: {
          title: '',
          description: '',
          isDone: false,
          poster: '',
          category: ''
        }
      }
    },
    computed: {
      filteredBooks() {
        if(this.category === 'All Categories'){
          return this.books;
        } else {
          return this.books.filter((item) => {
            return item.category === this.category;
            });
        }
      }
    },
    methods: {
      addBook() {
        this.books.push(this.form);
        this.isCreating = false;
        this.form = {
          title: '',
          description: '',
          isDone: false,
          poster: '',
          category: ''
        }
      }
    }
  }
</script>
