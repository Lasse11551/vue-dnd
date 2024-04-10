<template>
    <div
        :id="id"
        class="board"
        @dragover.prevent
        @drop.prevent="drop"
    >
    <h3>{{ header }}</h3>
        <slot />
    </div>
</template>

<script>
export default {
    props: ['id', 'header'],
    methods: {
        drop: e => {
            const card_id = e.dataTransfer.getData('card_id');
            const card = document.getElementById(card_id);
            card.style.display="block"
            e.target.appendChild(card)
        }
    }
}
</script>