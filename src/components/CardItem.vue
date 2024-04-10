<template>
    <div 
        :id="id"
        class="card"
        :draggable="draggable"
        @dragstart="dragStart"
        @dragover.stop
    >
        <h4>{{ title }}</h4>
        <p>{{ description }}</p>
    </div>
</template>

<script>
export default {
    props: ['id', 'draggable','title', 'description'],
    methods: {
        dragStart: e => {
            const target = e.target;
            e.dataTransfer.setData('card_id', target.id);
            setTimeout(() => {
                target.style.display = "none"
            }, 0)
        }
    }
}
</script>