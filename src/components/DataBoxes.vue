<template>
    <div class="grid md:grid-cols-2 gap-4">
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New: </span>
                <span class="text-blue-900 font-medium">{{ numberWithCommas(stats.NewConfirmed) }}</span>
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total: </span>
                <span class="text-blue-900 font-medium">{{ numberWithCommas(stats.TotalConfirmed) }}</span>
            </div>
        </div>

        <div class="shadow-md bg-red-100 p-10 text-center rounded">
            <h3 class="text-3xl text-red-900 font-bold mb-4">Deaths</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New: </span>
                <span class="text-red-900 font-medium">{{ numberWithCommas(stats.NewDeaths) }}</span>
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total: </span>
                <span class="text-red-900 font-medium">{{ numberWithCommas(stats.TotalDeaths) }}</span>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: 'DataBoxes',
    props: {
        stats: {
            required: true,
        }
    },
    methods: {
        numberWithCommas(num) {
            return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }
    }
}
</script>