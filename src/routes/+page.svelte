<script lang="ts">
  import { walletClient } from "$lib/stores";
  import { hooks } from "svelte-preprocess-react";
  import { usePrivy } from "@privy-io/react-auth";

  const privyStore = hooks(() => usePrivy());
</script>

<p>{$walletClient.account?.address}</p>

{#if $privyStore}
  {@const { logout } = $privyStore}
  <button on:click={logout}> Logout </button>

  <h2>Privy Config</h2>
  <code>
    {JSON.stringify($privyStore?.user)}
  </code>
{/if}
