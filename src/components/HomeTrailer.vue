<template>
  <div class="container-fluid trailer">
    <div class="row">
      <div class="col-12">
        <div class="trailer-video text_align">
          <iframe
            width="100%"
            height="400"
            src="https://www.youtube.com/embed/ESEUoa-mz2c"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
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
    align-items: flex-start; //utilizzo anche il display flex per centrare il testo a metà del contenuto
    flex-direction: column;
    justify-content: center;
    width: 50%;
    position: absolute;
    bottom: 7px;
    height: 25rem; //ho provato con line-height ma tutte le righe della trama prendevano lo spazio assegnato
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
