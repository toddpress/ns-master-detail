<page>
  <actionBar title="{flick.title}" />

  <scrollView>
    <stackLayout>
      <img margin="0" stretch="aspectFill" src="{flick.image}" />
      <stackLayout padding="10 20">
        {#each flick.details as details}
          <stackLayout>
            <label
              marginTop="10"
              fontSize="16"
              fontWeight="700"
              class="text-primary"
              textWrap="true"
              text="{details.title}"
            />
            <label
              fontSize="14"
              class="text-secondary"
              textWrap="true"
              text="{details.body}"
            />
          </stackLayout>
        {/each}
      </stackLayout>
    </stackLayout>
  </scrollView>
</page>
<script>
  import { FlickService } from '../services/FlickService'
  export let flickId

  let flick = FlickService.getInstance().getFlick(flickId)
</script>
