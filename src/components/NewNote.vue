<template>
    <div class="new-note">
        <label>Priority</label>
        <select v-model="note.priority">
            <option value="middle">Middle</option>
            <option value="difficult">Difficult</option>
            <option value="very-difficult">Very difficult</option>
        </select>
        <label>Title</label>
        <input v-model="note.title" type="text" />
        <label>Description</label>
        <textarea v-model="note.descr"></textarea>
        <button class="btn btnPrimary" @click="addNote">New note</button>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            required: true
        }
    },
    methods: {
        addNote() {
            this.$emit('addNote', this.note);
        }
    }
}
</script>

<style lang="scss">
.new-note {
    text-align: center;
    button {
        margin: 20px 0;
    }
}
</style>