<template>
    <div>
        <b-navbar toggleable="lg" type="light" variant="light" v-if="tag === 'highchart'">
            <b-navbar-brand to="/" class="logos">
                <img src="@/assets/highcharts_logo.png" width="75%" alt="Highcharts Logo">
                <img src="@/assets/nuxt.svg" width="18%" @click="$router.push('/')">
            </b-navbar-brand>
            <b-navbar-toggle target="nav-collapse"/>

            <b-collapse id="nav-collapse" is-nav right>
                <b-navbar-nav class="ml-auto" right>
                    <select v-model="selectedChart" class="form-control text-center"
                            @change="$emit('chartSelected', selectedChart)"
                    >
                        <option value="" disabled selected>
                            Select Chart
                        </option>
                        <option v-for="chart in charts" :key="chart.name" :value="chart">
                            {{ chart.displayName }}
                        </option>
                    </select>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>
        <b-navbar toggleable="lg" type="light" variant="light" v-else>
            <b-navbar-brand to="/" class="logos">
                <img src="@/assets/nuxt.svg" width="18%" @click="$router.push('/')">
            </b-navbar-brand>
            <b-navbar-toggle target="nav-collapse"/>

            <b-collapse id="nav-collapse" is-nav right>
                <b-navbar-nav class="ml-auto" right>

                </b-navbar-nav>
            </b-collapse>

        </b-navbar>
    </div>
</template>

<script>
export default {
    props: {
        charts: {
            type: Array,
            default: () => []
        },
        tag: '',
    },
    data () {
        return {
            selectedChart: ''
        }
    }
}
</script>

<style scoped>
.logos {
    width: 25%;
}
</style>
