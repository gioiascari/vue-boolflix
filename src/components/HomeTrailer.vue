<template>
  <div class="container-fluid trailer">
    <div class="row">
      <div class="col-12">
        <div class="trailer-video text_align">
          <iframe
            width="100%"
            height="400"
            src="https://www.youtube.com/embed/cTvQuB2lheE"
            title="dark-trailer"
            frameborder="0"
            allow="accelerometer; autoplay;"
          ></iframe>
          <div class="text-trailer d-flex">
            <div class="text-plot w-75">
              <h2>Dark</h2>
              <p>
                Children start vanishing from the German town of Winden,[13]
                bringing to light the fractured relationships, double lives, and
                the dark pasts of four families living there, and unfurling a
                mystery that spans four generations.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeTrailer",
};
</script>

<style lang="scss">
.trailer-video {
  position: relative;
  .text-trailer {
    align-items: flex-start;
    flex-direction: column;
    justify-content: center;
    width: 50%;
    position: absolute;
    bottom: 7px;
    height: 25rem;
    padding: 20px;
    background-image: linear-gradient(
      to left,
      rgba(255, 0, 0, 0),
      rgb(0, 0, 0)
    );
  }
}

.text_align {
  text-align: left;
}
</style>
