<script lang="ts">
  import List, { Item, Text, Graphic, Separator, Subheader } from '@smui/list';

  export let items;
</script>
<List>
  {#each items as item}
  <Item>
    <Text> {item} </Text>
  </Item>
  {/each}
</List>
