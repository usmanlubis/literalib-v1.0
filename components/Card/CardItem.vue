<template>
  <!-- <div
    :class="['item-book card d-flex align-items-start border-bottom pt-3 pb-4', isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12'
    ]"
  >
    <input
      id="book"
      v-model="localbook.isDone"
      type="checkbox"
      name="status"
      class="me-2 mt-2"
      :checked="book.isDone"
    >
    <div
      :class="['d-flex flex-column', book.isDone ? 'text-decoration-line-through fst-italic' : ''
      ]"
    >
      <div class="title-book mb-1">
        {{ book.title }}
      </div>
      <div class="description-book small text-muted">
        {{ book.description }}
      </div>
    </div>
  </div> -->


  <div
    :class="['item-book card d-flex align-items-start border-bottom pt-3 pb-4', isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12'
    ]" style="width: 18rem;">
    <img :src="book.poster" class="card-img-top book-poster" :alt="book.title" />
    <div class="card-body">
      <h5 class="card-title">{{  book.title  }}</h5>
      <p class="card-text">{{  book.description  }}</p>
      <NuxtLink to="#" class="btn btn-primary">Edit</NuxtLink>
      <button type="button" class="btn btn-danger">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    book: {
      type: Object,
      default(){
        return {}
      }
    },
    isGrid: {
      type: Boolean,
      required: true,
      default: false,
    }
  },
  computed: {
    localbook: {
      get(){
        return this.book;
      },
      set(value){
        this.$emit('update:book', value);
      }
    }
  }
}
</script>

<style>

</style>
