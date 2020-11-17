<template>
<div class="editor">
    <editor-menu-bubble :editor="editor" :keep-in-bounds="keepInBounds" v-slot="{ commands, isActive, menu }">
        <div class="menububble" :class="{ 'is-active': menu.isActive }" :style="`left: ${menu.left}px; bottom: ${menu.bottom}px;`">

            <button class="menububble__button" :class="{ 'is-active': isActive.bold() }" @click="commands.bold">
                <icon name="bold" size="small" />
            </button>
            <button class="menububble__button" :class="{ 'is-active': isActive.italic() }" @click="commands.italic">
                <icon name="italic" size="small" />
            </button>
            <button class="menububble__button" :class="{ 'is-active': isActive.code() }" @click="commands.code">
                <icon name="code" size="small" />
            </button>

        </div>
    </editor-menu-bubble>
    <editor-content class="editor__content" :editor="editor" />
</div>
</template>

<script>
import Icon from './Icon'

import {
    Editor,
    EditorContent,
    EditorMenuBubble
} from 'tiptap'
import {
    Blockquote,
    BulletList,
    CodeBlock,
    HardBreak,
    Heading,
    ListItem,
    OrderedList,
    TodoItem,
    TodoList,
    Bold,
    Code,
    Italic,
    Link,
    Strike,
    Underline,
    History,
} from 'tiptap-extensions'
export default {
    components: {
        EditorContent,
        EditorMenuBubble,
        Icon
    },
    props: {
        propContent: {
            type: String,
            required: true
        }
    },
    watch : {
        propContent: function(newVal, oldVal){
            console.log("newVal: " + newVal + ", oldVal: " + oldVal);
            if (newVal !== oldVal){
                console.log("editor content: " +this.editor.content)
                this.editor.setContent(newVal);
            }
        }
    },
    data() {
        return {
            keepInBounds: true,
            editor: new Editor({
                extensions: [
                    new Blockquote(),
                    new BulletList(),
                    new CodeBlock(),
                    new HardBreak(),
                    new Heading({
                        levels: [1, 2, 3]
                    }),
                    new ListItem(),
                    new OrderedList(),
                    new TodoItem(),
                    new TodoList(),
                    new Link(),
                    new Bold(),
                    new Code(),
                    new Italic(),
                    new Strike(),
                    new Underline(),
                    new History(),
                ],
                
            }),
        }
    },
    beforeDestroy() {
        this.editor.destroy()
    },

}
</script>

<style>

</style>
