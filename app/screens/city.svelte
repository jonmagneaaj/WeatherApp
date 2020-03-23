<script>
    export let location
    export let city
</script>


<flexBoxLayout class='tile'>   
    {#if location}
        <!-- content here -->
        <label class='h1 title' text='{location.name}' /> 
        {#if (`${location.weather[0].main}` === 'Clouds')}
                <image class='img' src='~/images/clouds.png' stretch='none'/>
        {:else if (`${location.weather[0].main}` === 'Clear')}
                <image class='img' src='~/images/clear.png' stretch='none'/>
        {:else if (`${location.weather[0].main}` === 'Rain')}
                <image class='img' src='~/images/rain.png' stretch='none'/>
        {:else if (`${location.weather[0].main}` === 'Drizzle')}
                <image class='img' src='~/images/drizzle.png' stretch='none'/>
        {:else if (`${location.weather[0].main}` === 'Snow')}
                <image class='img' src='~/images/snow.png' stretch='none'/>
        {:else if (`${location.weather[0].main}` === 'Thunderstorm')}
                <image class='img' src='~/images/thunderstorm.png' stretch='none'/>
        {:else if (`${location.weather[0].main}` === 'Mist' || 'Smoke' || 'Haze' || 'Dust' || 'Fog' || 'Sand' || 'Dust' || 'Ash' || 'Squall' || 'Tornado')}
                <image class='img' src='~/images/smog.png' stretch='none'/>
        {:else}
                <label class='bory' text='{location.weather[0].main}' />
        {/if}
        <label class='bory' text='{location.weather[0].description}' />
        <label class='bory' text='{Math.round(location.main.temp)}c' />
        <label class='bory' text='{location.wind.speed} m/s' />
        <label class='bory' text='{location.sys.country}' />
    {:else}
        <!-- else content here -->
    {/if} 
</flexBoxLayout>

<style>
    .tile{
        background-color: #517eff;
        border-radius: 20px;
        width: 40%;

        justify-content: center;
        align-items: center;
        flex-direction: column;

        color: white;
        padding: 20px;
    }

    .bory{
        font-weight: 600;
    }

    .title{
        color: white;
    }

    .img{
        margin: 2%;
    }

    .h1{
        font-weight: 800;
    }


</style>
