<script>
  export let field = null;

  const dynamicField = field;

  const isNotConfiguredProperly =
    !field || (!dynamicField.value && !dynamicField.src);

  let hasFile = false;
  let linkText = null;
  let href = null;

  if (!isNotConfiguredProperly) {
    const file = dynamicField.src ? field : dynamicField.value;

    if (file) {
      hasFile = true;
      linkText = file.title || file.displayName;
      href = file.src;
    }
  }
</script>

{#if hasFile}
  <a href={href}>
    <slot> {linkText} </slot>
  </a>
{/if}
