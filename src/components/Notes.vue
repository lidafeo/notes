<template>
    <div class="notes">
        <div class="note" 
            :class="{ full: !grid, difficult: note.priority=='difficult', veryDifficult: note.priority=='very-difficult'}" 
            v-for="(note, index) in notes" 
            :key="index">
            <div class="note-header" :class="{ full: !grid }">
                <p @click="editNote(index)"> {{ note.title }} </p>
                <input type="text" style="display: none;">
                <p style="cursor: pointer;" @click="removeNote(index)">x</p>
            </div>
            <div class="note-body">
                <p> {{ note.descr }} </p>
                <span> {{ note.date }} </span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        notes: {
            type: Array,
            required: true
        },
        grid: {
            type: Boolean,
            required: true
        }
    },
    methods: {
        removeNote(index) {
            console.log(`Note id - ${index} removed`);
            this.$emit('remove', index);
        },
        editNote(index) {

        }
    }
}
</script>

<style lang="scss">
.notes {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}
.note {
    width: 48%;
    padding: 18px 20px;
    margin-bottom: 20px;
    background-color: #ffffff;
    transition: all .25s cubic-bezier(.02, .01, .47, 1);
    box-shadow: 0 30px 30px rgba(0, 0, 0, .02);
    &:hover {
        box-shadow: 0 30px 30px rgba(0, 0, 0, .04);
        transform: translate(0, -6px);
        transition-delay: 0s !important;
    }
    &.full {
        width: 100%;
    }
    &.difficult {
        background-color: #feffa7 !important;
    }
    &.veryDifficult {
        background-color: #f8b5a5 !important;
    }
}
.note-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    h1 {
        font-size: 32px;
    }
    p {
        font-size: 22px;
        color: #5731dd
    }
    svg {
        margin-right: 12px;
        color: #999999;
        &.active {
            color: rgb(62, 72, 204);
        }
        &:last-child {
            margin-right: 0;
        }
    }
    &.full {
        justify-content: center;
        p {
            margin-right: 16px;
            &:last-child {
                margin-right: 0;
            }
        }
    }
}
.note-body {
    p {
        margin: 20px 0;
    }
    span {
        font-size: 14px;
        color: #999999;
    }
}
</style>