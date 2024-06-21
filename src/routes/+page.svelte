<script lang="ts">
  import Drawer, {
    AppContent,
    Content,
    Header,
    Title,
    Subtitle,
    Scrim,
  } from '@smui/drawer';
  import SvgIcon from '@jamescoyle/svelte-icon';
  import { mdiInbox } from '@mdi/js';
  import Button, { Label } from '@smui/button';
  import Textfield from '@smui/textfield';
  import { invoke } from "@tauri-apps/api/core";

  import MyList from "./mylist.svelte";
  import Terminal from "./terminal.svelte";

  let name = "";
  let greetMsg = "";

  let items = genitems(1000);


  function genitems(count) {
    let v = []; 
    for (let i = 0; i < count; i++) {
      v.push(`test${i}`);
    }
    return v
  }
  let open = false;

  async function greet() {
    greetMsg = await invoke("greet", { name });
  }
</script>

<div class="container">
  <div class="drawer-container">
    <!-- Don't include fixed={false} if this is a page wide drawer.
      It adds a style for absolute positioning. -->
      <Drawer variant="modal" fixed={false} bind:open>
        <Content>
          <MyList bind:items />
        </Content>
      </Drawer>

      <!-- Don't include fixed={false} if this is a page wide drawer.
        It adds a style for absolute positioning. -->
        <Scrim fixed={false} />
        <AppContent class="app-content">
        <main class="main-content">
          <Button on:click={() => (open = !open)}>
            <Label>Toggle Drawer</Label>
          </Button>
          <br />
        </main>
        </AppContent>


        <Terminal />
  </div>
</div>
