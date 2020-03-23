<script>
    const appSettings = require("tns-core-modules/application-settings")
    import { onMount } from 'svelte'
    import City from './screens/City.svelte'
    const key = '3f120a4d3b9f2068564a054fe88ee464'
    let city
    let location

    const setDefault = () => {
        appSettings.setString('default-city', city)
    }

    const getData  = () => {
        let url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${key}&units=metric`
        console.log('##### URL: ' + url)
        fetch(url)
            .then(response => response.json())
            .then( json => {
                console.log('###### JSON: ' + json)
                location = json
            })
            .catch( error => console.log('###### ERROR: ' + error))
    }

    onMount( () => {
        city = appSettings.getString('default-city') ? appSettings.getString('default-city') : null
        if(city){
            getData()
        }
    })


</script>

<page>     
    <actionBar title='Weather' />
        <stackLayout class='centered'>
            <label class='h1 text-center' text='choose city' />
            <searchBar bind:text='{city}' on:submit={ () => getData() } hint='Type city' editable='{true}' />
            <button text='set default city' class='primary' on:tap={setDefault} />
            <City {city} location={location} />
        </stackLayout>
</page> 

<style>
</style>