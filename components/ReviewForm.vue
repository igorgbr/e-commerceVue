app.component('review-form', {
  template:
    /*html*/
    `<form class="review-form" @submit.prevent="onSubmit">
    <h3>Leave a review</h3>

    <label for="name">Name:</label>
        <input id="name" v-model="name">
    
    <label for="review">Review:</label>
        <textarea id="review" v-model="review">></textarea>
    
    <label for="rating">Rating:</label>
        <select id="rating" v-model.number="rating">>
            <option>5</option>
            <option>4</option>
            <option>3</option>
            <option>2</option>
            <option>1</option>
        </select>

        <div>
        <p>Would you recommend this product?</p>
        <input type="checkbox" id="recomended" name="recomended" v-model="recomended">
      </div>

    <input class="button" type="submit" value="submit">
    
    </form>`,
  data() {
    return {
      name: '',
      review: '',
      rating: null,
      recomended: false
    };
  },
  methods: {
      onSubmit() {
          if(this.name === '' || this.review === '' || this.rating === null) {
              alert('Empty form')
              return
          }
          let productReview = {
              name: this.name,
              review: this.review,
              rating: this.rating,
              recomended: this.recomended
          }
          this.$emit('review-submitted', productReview)


          this.name = ''
          this.review = ''
          this.rating = null
          this.recomended = false
      }
  }
});
