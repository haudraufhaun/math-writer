<template>
  <VueEditor :editor="editor" />
</template>

<script>
import { defineComponent } from "vue";
import { Editor, rootCtx, defaultValueCtx } from "@milkdown/core";
import { nord } from "@milkdown/theme-nord";
import { VueEditor, useEditor } from "@milkdown/vue";
import { commonmark } from "@milkdown/preset-commonmark";
import { math } from "@milkdown/plugin-math";
export default defineComponent({
  name: "Milkdown",
  components: {
    VueEditor,
  },
  setup: () => {
    const editor = useEditor((root) =>
      Editor.make()
        .config((ctx) => {
          ctx.set(rootCtx, root);
          ctx.set(defaultValueCtx, "# Welcome to MathWriter 🧮");
        })
        .use(nord)
        .use(commonmark)
        .use(math)
    );
    return {
      editor,
    };
  },
});
</script>
<style></style>
