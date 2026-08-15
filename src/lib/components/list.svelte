<script lang="ts" generics="T">
  import type { Snippet } from "svelte";
  import type { HTMLAttributes } from "svelte/elements";

  type Props = {
    separator?: Snippet | string;
    items: T[];
    children: Snippet<[T, number]>;
  } & Omit<HTMLAttributes<HTMLElement>, "children">;
  const { separator = "|", items, children, ...props }: Props = $props();
</script>

<div {...props}>
  {#each items as item, i}
    {#if i > 0 && i < items.length}
      {#if typeof separator === "string"}
        <span>
          {separator}
        </span>
      {:else}
        {@render separator()}
      {/if}
    {/if}
    {@render children(item, i)}
  {/each}
</div>
