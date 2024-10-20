<script>
    import { currentChapter, currentPage } from '../store.js';
    import { buttonVariants } from "$lib/components/ui/button"
    import * as Card from "$lib/components/ui/card/index.js";
    import * as Carousel from "$lib/components/ui/carousel/index.js";
    import * as Dialog from "$lib/components/ui/dialog";
    import * as Select from "$lib/components/ui/select";
    import { Textarea } from "$lib/components/ui/textarea";

    let averageRating = 4.7;
    let totalReviews = 299;
    let reviews = [
      { rating: 5, text: "Currently, I'm on the third book, and absolutely love and enjoy how everything is playing out. I adore the diversity of characters, landscapes, etc. I would highly recommend this series to others who are also lovers of dragons! This series had me so enthralled to the point where I intentionally searched the end of some of the characters. Overall, great series and I absolutely enjoy the passion in these books." },
      { rating: 4, text: 'Really enjoyed it.' },
      // Add more reviews
    ];

    let userEntry = '';
    let ratingEntry = {value: 1, label: '1'};
    let userReview = {text: '', score: 0}

    function addReview() {
      if(userEntry != '') {
        userReview.text = userEntry;
        userReview.score = ratingEntry.value;
      }
    }
</script>

<style>
    .review-item {
        margin-bottom: 15px;
    }

    .rating {
        color: #ffdd57;
    }

    h2, h3 {
        margin-bottom: 10px;
    }

    .add-review button {
      padding: 8px 12px;
      border-radius: 5px;
      background-color: #ffdd57;
      color: #000;
      border: none;
      cursor: pointer;
    }
</style>

<div class="main">
    <h2>Book Reviews</h2>
    <p class="positionMarking">Current Chapter: {$currentChapter}, Current Page: {$currentPage}</p>
    <h4>
        Average Rating: <span class="rating">{averageRating} / 5</span> ({totalReviews} reviews)
    </h4>
    <Carousel.Root class="w-3/4">
        <Carousel.Content>
          {#each reviews as review}
            <Carousel.Item>
              <div class="p-1">
                <Card.Root>
                  <Card.Content
                    class="flex aspect-video items-center justify-center p-6"
                  >
                    <div class="">
                        <div class="rating">Rating: {review.rating} / 5</div>
                        <p>{review.text}</p>
                    </div>
                  </Card.Content>
                </Card.Root>
              </div>
            </Carousel.Item>
          {/each}
        </Carousel.Content>
        <Carousel.Previous />
        <Carousel.Next />
      </Carousel.Root>
      
      <h4>Your Review</h4>
      <div class="mb-4">
        <Dialog.Root>
          <Dialog.Trigger class={buttonVariants({ variant: "outline" })}
            >Create Review</Dialog.Trigger
          >
          <Dialog.Content class="sm:max-w-[425px]" style="background: linear-gradient(135deg, #2b5876, #4e4376);">
            <Dialog.Header>
              <Dialog.Title>Create Review</Dialog.Title>
              <Dialog.Description>
                Create your review of Eragon here. Click create when you're done.
              </Dialog.Description>
            </Dialog.Header>
            <div class="">
              <Textarea bind:value={userEntry} placeholder="Write a review..." style="color: white" class="mb-4"/>
              <Select.Root selected={ratingEntry}>
                <Select.Trigger class="" style="color: white">
                  <Select.Value placeholder="Rating" />
                </Select.Trigger>
                <Select.Content>
                  <Select.Item value=1>1 Star</Select.Item>
                  <Select.Item value=2>2 Stars</Select.Item>
                  <Select.Item value=3>3 Stars</Select.Item>
                  <Select.Item value=4>4 Stars</Select.Item>
                  <Select.Item value=5>5 Stars</Select.Item>
                </Select.Content>
              </Select.Root>
              <div class="add-review mt-4"><button on:click={addReview}>Create</button></div>
            </div>
          </Dialog.Content>
        </Dialog.Root>
      </div>
      {#if userReview.text == ''}
        <p>No review left. Leave a review once you complete the book!</p>
      {:else}
        <div class="rating">Rating: {userReview.score} / 5</div>
        <p>{userReview.text}</p>
      {/if}
</div>
