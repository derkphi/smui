<script lang="ts">
  import {Label} from '@smui/common';
  import Button from '@smui/button';
  import {AppContent} from '@smui/drawer';
  import Card from '@smui/card';
  import LayoutGrid, { Cell } from '@smui/layout-grid';
  import Accordion, { Panel, Header as PanelHeader, Content as PanelContent } from '@smui-extra/accordion';

  import AppHeader from '../components/appHeader.svelte';
  import AppNav from '../components/appNav.svelte';
  import MediaQuery from '../components/MediaQuery.svelte';

  let navOpen = false;
  
  let lw : number;
  let cw : number;
  let ww : number;
</script>
<MediaQuery query="(max-width: 599px)" let:matches>
  <AppHeader modal={matches} on:menuClick={() => navOpen = !navOpen}/>
  <AppNav modal={matches} open={navOpen}/>
</MediaQuery>
<AppContent class="mdc-top-app-bar--fixed-adjust">
  <LayoutGrid>
    <Cell spanDevices={{ desktop: 6, tablet: 8, phone: 4 }}>
      <div bind:clientWidth={cw}>
        <Card padded>
          <p>Card 1</p>
          <p>Window width: {ww}</p>
          <p>Layout grid width: {lw}</p>
          <p>Card width: {cw}</p>
        </Card>
      </div>
      <div class="card-spacer"/>
      <Card padded>Card 2</Card>
      <div class="card-spacer"/>
      <Accordion>
        <Panel>
          <PanelHeader>Panel 1</PanelHeader>
          <PanelContent>
            The content for panel 1.
            <ul>
              <li>Some</li>
              <li>List</li>
              <li>Items</li>
            </ul>
          </PanelContent>
        </Panel>
      </Accordion>
    </Cell>
    <Cell spanDevices={{ desktop: 6, tablet: 8, phone: 4 }}>
      <Card padded>Card 3</Card>
      <div class="card-spacer"/>
      <Card padded>Card 4</Card>
      <div class="card-spacer"/>
      <Card padded>Card 5</Card>
    </Cell>
    <Cell spanDevices={{ desktop: 12, tablet: 8, phone: 4 }}>
      <div class="action-row">
        <div class="apply-button">
          <Button variant="raised">
            <Label>Apply</Label>
          </Button>
        </div>
        <Button variant="raised">
          <Label>Reload</Label>
        </Button>
      </div>
    </Cell>
  </LayoutGrid>
</AppContent>

<style>
  :global(body) {
    width: 100vw;
    margin: 0px;
    display: flex;
  }

  :global(.mdc-drawer-app-content) {
    width: 100%;
  }

  .card-spacer {
    margin-bottom: 15px;
  }

  .action-row {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
  }

  .apply-button {
    margin-right: 15px;
  }
</style>