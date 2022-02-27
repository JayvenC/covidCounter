<template>
    <div class="grid md:grid-cols-2 gap-4">
        <div class="shadow-md bg-red-100 p-10 text-center rounded">
            <h3 class="text-3xl text-red-600 font-bold mb-4">Cases</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New (Today):</span>
                {{addCommas(stats.NewConfirmed)}}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{addCommas(stats.TotalConfirmed)}}
            </div>
        </div>
        <div class="shadow-md bg-red-400 p-10 text-center rounded">
            <h3 class="text-3xl text-red-700 font-bold mb-4">Deaths</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New (Today):</span>
                {{addCommas(stats.NewDeaths)}}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{addCommas(stats.TotalDeaths)}}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Boxes',
    props: ['stats'],
    methods: {
        addCommas(x) {
           return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',') 
        }
    }

}
</script>
