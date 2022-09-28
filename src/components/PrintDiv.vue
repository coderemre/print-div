<template>
  <div class="print_div">
    <h2 class="m-bottom-20 f-size40">print-div</h2>
    <p class="m-bottom-20 f-size16">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
      Lorem Ipsum has been the industry's standard dummy text ever since the
      1500s, when an unknown printer took a galley of type and
    </p>
    <div class="print_area" id="printSection">
      <h1 class="t-center m-bottom-20 f-size30">Print Area</h1>
      <p class="m-bottom-10 f-size16">
        Lorem Ipsum is simply dummy text of the printing and typesetting
        industry. Lorem Ipsum has been the industry's standard dummy text ever
        since the 1500s, when an unknown printer took a galley of type and
        scrambled it to make a type specimen book. It has survived not only five
        centuries, but also the leap into electronic typesetting, remaining
        essentially unchanged.
      </p>
      <p class="m-bottom-10 f-size16 danger_color">
        It was popularised in the 1960s with the release of Letraset sheets
        containing Lorem Ipsum passages, and more recently with desktop
        publishing software like Aldus PageMaker including versions of Lorem
        Ipsum.
      </p>
      <p class="f-size16">
        It was popularised in the 1960s with the release of Letraset sheets
        containing Lorem Ipsum passages, and more recently with desktop
        publishing software like Aldus PageMaker including versions of Lorem
        Ipsum.
      </p>

      <button
        class="btn primary m-top-20"
        @click="print($event, 'printSection')"
      >
        Print
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
const print = (event: any, divID: string) => {
  console.log(event)
  var printCon: any = document.getElementById(divID)
  if (printCon) {
    event.target.classList.add('hide')
    var printContents = printCon.innerHTML
    event.target.classList.remove('hide')
    var pop: any = window.open(
      window.location.href,
      '_blank',
      'toolbar=none,scrollbars=yes,resizable=none,top=0,left=0'
    )
    pop.addEventListener('DOMContentLoaded', () => {
      pop.document.body.innerHTML = printContents
      pop.print()
      setTimeout(function () {
        pop.close()
      }, 500)
    })
    return true
  } else {
    return false
  }
}
</script>

<style lang="scss">
.print_div {
  top: 200px;
  @media (max-width: 1280px) {
    padding: 0 20px;
  }

  .print_area {
    padding: 10px 20px 30px;
    border: 1px solid var(--primaryColor);
  }
  .v-enter-active,
  .v-leave-active {
    transition: transform 1s ease-in-out;
  }
  .v-enter-from {
    transform: translateY(1000%);
  }
  .v-enter-to {
    transform: translateY(0%);
  }
  .v-leave-from {
    transform: translateY(0%);
  }
  .v-leave-to {
    transform: translateY(-1000%);
  }
}
</style>
