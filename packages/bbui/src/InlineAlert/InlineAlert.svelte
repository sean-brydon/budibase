<script>
  import "@spectrum-css/inlinealert/dist/index-vars.css"
  import Button from "../Button/Button.svelte"

  export let type = "info"
  export let header = ""
  export let message = ""
  export let onConfirm = undefined

  $: icon = selectIcon(type)

  function selectIcon(alertType) {
    switch (alertType) {
      case "error":
      case "negative":
        return "Alert"
      case "success":
        return "CheckmarkCircle"
      case "help":
        return "Help"
      default:
        return "Info"
    }
  }
</script>

<div class="spectrum-InLineAlert spectrum-InLineAlert--{type}">
  <svg
    class="spectrum-Icon spectrum-Icon--sizeM spectrum-InLineAlert-icon"
    focusable="false"
    aria-hidden="true"
  >
    <use xlink:href="#spectrum-icon-18-{icon}" />
  </svg>
  <div class="spectrum-InLineAlert-header">{header}</div>
  <div class="spectrum-InLineAlert-content">{message}</div>
  {#if onConfirm}
    <div class="spectrum-InLineAlert-footer">
      <Button secondary on:click={onConfirm}>OK</Button>
    </div>
  {/if}
</div>

<style>
  .spectrum-InLineAlert {
    --spectrum-semantic-negative-border-color: #e34850;
    --spectrum-semantic-positive-border-color: #2d9d78;
    --spectrum-semantic-positive-icon-color: #2d9d78;
    --spectrum-semantic-negative-icon-color: #e34850;
    min-width: 100px;
  }
</style>
