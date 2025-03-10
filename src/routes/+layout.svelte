<script lang="ts">
  import "../app.css";
  let { children } = $props();
</script>

<div class="min-h-screen md:max-w-md max-w-screen flex flex-col flex-0 mx-auto">
  {@render children()}
</div>
