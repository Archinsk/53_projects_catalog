<template>
  <div class="card">
    <template v-if="!horizontal">
      <div v-if="header" class="card-header">
        <slot name="card-header"></slot>
      </div>
      <template v-if="imagePosition === 'top' || imagePosition === 'full'">
        <slot name="card-image-top"></slot>
      </template>
      <div v-if="!noBody" class="card-body">
        <slot name="card-body"></slot>
      </div>
      <template v-if="imagePosition === 'bottom'">
        <slot name="card-image-bottom"></slot>
      </template>
      <div v-if="footer" class="card-footer">
        <slot name="card-footer"></slot>
      </div>
    </template>
    <template v-if="horizontal">
      <div class="row g-0">
        <div class="col-4">
          <template v-if="imagePosition === 'top' || imagePosition === 'full'">
            <slot name="card-image-top"></slot>
          </template>
        </div>
        <div class="col-8">
          <div v-if="!noBody" class="card-body">
            <slot name="card-body"></slot>
          </div>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "VbCard",
  props: {
    cardData: Object,
    header: Boolean,
    noBody: Boolean,
    footer: Boolean,
    imagePosition: String,
    horizontal: Boolean,
  },
};
</script>
