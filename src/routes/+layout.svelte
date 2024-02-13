<script lang="ts">
  import { PrivyProvider } from "@privy-io/react-auth";
  import { used } from "svelte-preprocess-react";
  import { mainnet } from "viem/chains";

  import WalletClientGuard from "$lib/components/WalletClientGuard.svelte";
  import ConnectGuard from "$lib/components/ConnectGuard.svelte";

  import { PUBLIC_PRIVY_APP_ID } from "$env/static/public";

  // does nothing just prevents unused tsc warning
  used(PrivyProvider);
</script>

<div>
  <h1>Privy Svelte Example</h1>

  <react:PrivyProvider
    appId={PUBLIC_PRIVY_APP_ID}
    config={{
      defaultChain: mainnet,
      supportedChains: [mainnet],
      loginMethods: ["email", "wallet"],
    }}
  >
    <ConnectGuard>
      <WalletClientGuard>
        <slot />
      </WalletClientGuard>
    </ConnectGuard>
  </react:PrivyProvider>
</div>
