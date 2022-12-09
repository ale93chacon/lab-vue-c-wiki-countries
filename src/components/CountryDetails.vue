<template>
    <div class="col-7">
        
        <img :src="' https://www.geonames.org/flags/x/'  +  countryDetails.alpha2Code.toLowerCase() + '.gif'"
        alt="country flag" style="width: 300px" />
        <h1>{{countryDetails.name.common}}</h1>
        <table class="table">
            <thead></thead>
            <tbody>
                <tr>
                    <td style="width: 30%">Capital</td>
                    <td>{{countryDetails.capital[0]}}</td>
                </tr>
                <tr>
                    <td>Area</td>
                    <td>
                        {{countryDetails.area}} km <sup>2</sup>
                    </td>
                </tr>
                <tr >
                    <td >Borders</td>
                    <td>
                        <ul  v-for="(border, index) in countryDetails.borders" :key="index">
                            <li ><router-link :to="`/${countryDetails.alpha3Code}`">{{border}}</router-link></li>
                        
                        </ul>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
import countries from "../../public/countries.json";
export default {
    data(){
    return{
        countries: countries,
    }  
},
    computed: {
        countryDetails() {
            const countryId = this.$route.params.alpha3Code;
            return this.countries.find(function(country){
                if (country.alpha3Code === countryId){
                    return true;
                }
                else{
                    return false;
                }
            });

        }
    },
    mounted() {
        // NO se tiene que hacer en mounted
        console.log(this.$route.params)
    }
}</script>


