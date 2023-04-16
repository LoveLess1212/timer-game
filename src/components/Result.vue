<template>
    <div>
        <h1>Result</h1>
        <p>your score is {{ score }}ms</p>
        <p>your rank is {{ rank }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            rank: null
        }
    },
    props: ['score']
    , mounted() {
        if (this.score < 250) {
            this.rank = 'Master'
        } else if (this.score < 500) {
            this.rank = 'Expert'
        } else {
            this.rank = 'Newbie'
        }
    }
}

</script>
