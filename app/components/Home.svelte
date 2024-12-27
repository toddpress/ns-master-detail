<page>
  <actionBar title="NativeFlix" />
  <!-- Add this 👇 -->
<stackLayout height="100%">
    <listView
      height="100%"
      separatorColor="transparent"
      items="{flicks}"
      on:itemTap="{onFlickTap}"
    >
      <template let:item>
        <!-- Add this 👇 -->
        <gridLayout
          height="280"
          borderRadius="10"
          class="bg-secondary"
          rows="*, auto, auto"
          columns="*"
          margin="5 10"
          padding="0"
        >
          <image row="0" margin="0" stretch="aspectFill" src="{item.image}" />
          <label
            row="1"
            margin="10 10 0 10"
            fontWeight="700"
            class="text-primary"
            fontSize="18"
            text="{item.title}"
          />
          <label
            row="2"
            margin="0 10 10 10"
            class="text-secondary"
            fontSize="14"
            textWrap="true"
            text="{item.description}"
          />
        </gridLayout>
      </template>
    </listView>
  </stackLayout>
</page>

<script>
  import { navigate } from 'svelte-native'
  import { Template } from 'svelte-native/components'
  import { FlickService } from '../services/FlickService'

  import Details from './Details.svelte'

  let flicks = FlickService.getInstance().getFlicks()

// Add this 👇
function onFlickTap(event) {
  navigate({
    page: Details,
    props: { flickId: flicks[event.index].id }
  })
}
</script>
