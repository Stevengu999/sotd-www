<template>
  <div class="page-promoted-dapps">
    <PromotedDapps
      :description="description"
    />
  </div>
</template>

<script>
import { setPromotedDappsPage } from '~/helpers/mixins'
import PromotedDapps from '~/components/PromotedDapps'

export default {
  components: {
    PromotedDapps
  },
  mixins: [setPromotedDappsPage]
}
</script>

