<template>
    <div class="grid md:grid-cols-2 gap-4">
        <!-- cases -->
        <div class="shadow-md bg-red-100 p-10 text-center rounded">
            <h3 class="text-3xl text-red-900 font-bold mb-4">Cases</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{formatNum(stats.NewConfirmed)}}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{formatNum(stats.TotalConfirmed)}}
            </div>
        </div>
        <!-- Deaths -->
        <div class="shadow-md bg-red-200 p-10 text-center rounded">
            <h3 class="text-3xl text-red-900 font-bold mb-4">Deaths</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{formatNum(stats.NewDeaths)}}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{formatNum(stats.TotalDeaths)}}
            </div>
        </div>
    </div>
</template>

<script>
 export default {
     name: 'DataBoxes',
     props: ['stats'],
     methods: {
         formatNum (x) {
             return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
        } 
     }
 }
</script>
