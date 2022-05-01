<script lang="ts">
  import TopAppBar, {
    Row,
    Section,
    Title
  } from '@smui/top-app-bar';
  import IconButton from '@smui/icon-button';
  import { createEventDispatcher } from 'svelte';

  export let modal : Boolean = false;

	const dispatch = createEventDispatcher();
</script>

<TopAppBar variant="standard" class={modal ? "my-bar" : "my-bar top"}>
  <Row>
    <Section>
      {#if modal}
        <IconButton class="material-icons" on:click={() => {dispatch('menuClick')}}>menu</IconButton>
      {/if}
      <Title>Hanna</Title>
    </Section>
    <Section align="end" toolbar>
      <IconButton class="material-icons" aria-label="Download"
        >file_download</IconButton
      >
      <IconButton class="material-icons" aria-label="Print this page"
        >print</IconButton
      >
      <IconButton class="material-icons" aria-label="Bookmark this page"
        >bookmark</IconButton
      >
    </Section>
  </Row>
</TopAppBar>