<template>
    <div class= "habit-description">
        <v-card v-if="!habit.title">
            <v-card-title class="text-xs-center">
              <h2>You Don't Have Any Habits!</h2>
            </v-card-title>
            <v-card-text class="pt-0 text-xs-left">
                Click the <v-icon>add_circle</v-icon> to create a new Habit!
            </v-card-text>
        </v-card>
        <v-card v-else>
            <v-card-title class="text-xs-center">
                <v-icon large :color="habit.color">fiber_manual_record</v-icon>
                &ensp;<h2>{{habit.title}}</h2>
                &ensp;<v-icon :color="habit.color" @click.stop="deleteHabit" class="clickable">delete_forever</v-icon>

            </v-card-title>
            <v-card-text class="pt-0 text-xs-left">
                {{habit.description}}
            </v-card-text>
        </v-card>
    </div>  
</template>

<script>
export default {
    name: 'HabitDescription',
    props: {
        habit: {
            type: Object,
            default: {
                color: "blue",
                dates:{}
            }
        }
    },
    methods: {
        deleteHabit() {
            this.$store.commit('deleteHabit',{id: this.habit._id})
            location.reload()
            //console.log(`DELETE HABIT: `,this.habit)
        }
    }
}
</script>

<style>

</style>
