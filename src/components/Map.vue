<template>
    <div id="mapContainer" class="map-container"></div>
    <LightGallery ref=" LightGallery" :images="images" :showInput="false"></LightGallery>
</template>

<script>
import { ref } from 'vue';
import LightGallery from "./LightGallery.vue";
import mapboxgl from "mapbox-gl";
mapboxgl.accessToken = 'pk.eyJ1IjoicGluZ2lua28xMTEiLCJhIjoiY2xwZjZycnI0MWhwZzJpcGJyZWZjcDcwNSJ9.Ji2wJubeOahFITPXICGu_A';

export default {
    components: {
        LightGallery,
    },

    setup() {
        const images = ref([]);
        return {
            images,
        };
    },
    mounted() {
        const map = new mapboxgl.Map({
            container: 'mapContainer',
            style: 'mapbox://styles/mapbox/streets-v12',
            center: [20.438397, 49.123319],
            zoom: 10,
        });

        const popupBa1 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/blava1.jpg"><img src="/~xkubala/sivaStena/photos/blava1.jpg" alt="Bratislava1" style="width: 100%;"></a>' +
            '<p><strong>Bratislava1</strong>-Výhľad z budovy</p>'
        );

        const popupBa2 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/blava2.jpg"><img src="/~xkubala/sivaStena/photos/blava2.jpg" alt="Bratislava2" style="width: 100%;"></a>' +
            '<p><strong>Bratislava2</strong>-ESET Vnútro</p>'
        );

        const popupBa3 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/blava3.jpg"><img src="/~xkubala/sivaStena/photos/blava3.jpg" alt="Bratislava3" style="width: 100%;"></a>' +
            '<p><strong>Bratislava3</strong>-Výhľad z budovy</p>'
        );

        const popupFlo1 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/florence1.jpg"><img src="/~xkubala/sivaStena/photos/florence1.jpg" alt="Florencia1" style="width: 100%;"></a>' +
            '<p><strong>Florencia1</strong>-Výhľad z budovy</p>'
        );

        const popupFlo2 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/florence2.jpg"><img src="/~xkubala/sivaStena/photos/florence2.jpg" alt="Florencia2" style="width: 100%;"></a>' +
            '<p><strong>Florencia2</strong>- Maľba v galérii</p>'
        );

        const popupMt = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/ihrisko_martin.jpg"><img src="/~xkubala/sivaStena/photos/ihrisko_martin.jpg" alt="Martin" style="width: 100%;"></a>' +
            '<p><strong>Martin</strong>-Zimný štadión</p>'
        );

        const popupKk1 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/kezmarok1.jpg"><img src="/~xkubala/sivaStena/photos/kezmarok1.jpg" alt="Kežmarok1" style="width: 100%;"></a>' +
            '<p><strong>Kežmarok1</strong>-Príroda z iného pohľadu</p>'
        );

        const popupKk2 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/kezmarok2.jpg"><img src="/~xkubala/sivaStena/photos/kezmarok2.jpg" alt="Kežmarok2" style="width: 100%;"></a>' +
            '<p><strong>Kežmarok2</strong>-Mystické dievča</p>'
        );

        const popupKk3 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/kezmarok3.jpg"><img src="/~xkubala/sivaStena/photos/kezmarok3.jpg" alt="Kežmarok3" style="width: 100%;"></a>' +
            '<p><strong>Kežmarok3</strong>-Čarovné dievča</p>'
        );

        const popupKk4 = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/kezmarok4.jpg"><img src="/~xkubala/sivaStena/photos/kezmarok4.jpg" alt="Kežmarok4" style="width: 100%;"></a>' +
            '<p><strong>Kežmarok4</strong>-Krásne dievča</p>'
        );

        const popupStpleso = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/Štrbske_Pleso1.jpg"><img src="/~xkubala/sivaStena/photos/Štrbske_Pleso1.jpg" alt="Štrbské Pleso" style="width: 100%;"></a>' +
            '<p><strong>Štrbské Pleso</strong>-Pekná príroda</p>'
        );

        const popupPp = new mapboxgl.Popup({ offset: 25 }).setHTML(
            '<a href="/~xkubala/sivaStena/photos/poprad1.jpg"><img src="/~xkubala/sivaStena/photos/poprad1.jpg" alt="Poprad" style="width: 100%;"></a>' +
            '<p><strong>Poprad</strong>-Neidentifikovateľný muž</p>'
        );

        const markerBa1 = new mapboxgl.Marker()
            .setLngLat([17.10547116471864, 48.134316443637374])
            .setPopup(popupBa1)
            .addTo(map)
        markerBa1.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/blava1.jpg', name: 'Bratislava1', description: 'Výhľad z budovy', timestamp: '2022-10-05' },
                { url: '/~xkubala/sivaStena/photos/blava2.jpg', name: 'Bratislava2', description: 'ESET-vnútro', timestamp: '2022-03-23' },
                { url: '/~xkubala/sivaStena/photos/blava3.jpg', name: 'Bratislava3', description: 'Výhľad z budovy', timestamp: '2020-11-01' }
            ];
        });

        const markerBa2 = new mapboxgl.Marker()
            .setLngLat([17.106000, 48.134307])
            .setPopup(popupBa2)
            .addTo(map);
        markerBa2.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/blava1.jpg', name: 'Bratislava1', description: 'Výhľad z budovy', timestamp: '2022-10-05' },
                { url: '/~xkubala/sivaStena/photos/blava2.jpg', name: 'Bratislava2', description: 'ESET-vnútro', timestamp: '2022-03-23' },
                { url: '/~xkubala/sivaStena/photos/blava3.jpg', name: 'Bratislava3', description: 'Výhľad z budovy', timestamp: '2020-11-01' }
            ];
        });

        const markerBa3 = new mapboxgl.Marker()
            .setLngLat([17.1055454873267, 48.13396096212641])
            .setPopup(popupBa3)
            .addTo(map);
        markerBa3.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/blava1.jpg', name: 'Bratislava1', description: 'Výhľad z budovy', timestamp: '2022-10-05' },
                { url: '/~xkubala/sivaStena/photos/blava2.jpg', name: 'Bratislava2', description: 'ESET-vnútro', timestamp: '2022-03-23' },
                { url: '/~xkubala/sivaStena/photos/blava3.jpg', name: 'Bratislava3', description: 'Výhľad z budovy', timestamp: '2020-11-01' }
            ];
        });

        const markerFlo1 = new mapboxgl.Marker()
            .setLngLat([11.2561, 43.77087])
            .setPopup(popupFlo1)
            .addTo(map);
        markerFlo1.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/florence1.jpg', name: 'Florencia', description: 'Výhľad z budovy', timestamp: '2019-06-18' },
                { url: '/~xkubala/sivaStena/photos/florence2.jpg', name: 'Florencia-galéria', description: 'Maľba', timestamp: '2019-06-18' },
            ];
        });


        const markerFlo2 = new mapboxgl.Marker()
            .setLngLat([11.25538, 43.76934])
            .setPopup(popupFlo2)
            .addTo(map);
        markerFlo2.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/florence1.jpg', name: 'Florencia', description: 'Výhľad z budovy', timestamp: '2019-06-18' },
                { url: '/~xkubala/sivaStena/photos/florence2.jpg', name: 'Florencia-galéria', description: 'Maľba', timestamp: '2019-06-18' },
            ];
        });


        const markerMt = new mapboxgl.Marker()
            .setLngLat([18.912643, 49.074176])
            .setPopup(popupMt)
            .addTo(map);
        markerMt.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/ihrisko_martin.jpg', name: 'Martin', description: 'Zimný štadión', timestamp: '2018-06-20' },
            ];
        });


        const markerKk1 = new mapboxgl.Marker()
            .setLngLat([20.425776, 49.126720])
            .setPopup(popupKk1)
            .addTo(map);
        markerKk1.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/kezmarok1.jpg', name: 'Kežmarok1', description: 'Príroda z iného pohľadu', timestamp: '2019-10-02' },
                { url: '/~xkubala/sivaStena/photos/kezmarok2.jpg', name: 'Kežmarok2', description: 'Mystické dievča', timestamp: '2021-08-17' },
                { url: '/~xkubala/sivaStena/photos/kezmarok3.jpg', name: 'Kežmarok3', description: 'Čarovné dievča', timestamp: '2021-09-04' },
                { url: '/~xkubala/sivaStena/photos/kezmarok4.jpg', name: 'Kežmarok4', description: 'Krásne dievča', timestamp: '2021-08-29' }

            ];
        });

        const markerKk2 = new mapboxgl.Marker()
            .setLngLat([20.430058, 49.125223])
            .setPopup(popupKk2)
            .addTo(map);
        markerKk2.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/kezmarok1.jpg', name: 'Kežmarok1', description: 'Príroda z iného pohľadu', timestamp: '2019-10-02' },
                { url: '/~xkubala/sivaStena/photos/kezmarok2.jpg', name: 'Kežmarok2', description: 'Mystické dievča', timestamp: '2021-08-17' },
                { url: '/~xkubala/sivaStena/photos/kezmarok3.jpg', name: 'Kežmarok3', description: 'Čarovné dievča', timestamp: '2021-09-04' },
                { url: '/~xkubala/sivaStena/photos/kezmarok4.jpg', name: 'Kežmarok4', description: 'Krásne dievča', timestamp: '2021-08-29' }

            ];
        });

        const markerKk3 = new mapboxgl.Marker()
            .setLngLat([20.439615, 49.137597])
            .setPopup(popupKk3)
            .addTo(map);
        markerKk3.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/kezmarok1.jpg', name: 'Kežmarok1', description: 'Príroda z iného pohľadu', timestamp: '2019-10-02' },
                { url: '/~xkubala/sivaStena/photos/kezmarok2.jpg', name: 'Kežmarok2', description: 'Mystické dievča', timestamp: '2021-08-17' },
                { url: '/~xkubala/sivaStena/photos/kezmarok3.jpg', name: 'Kežmarok3', description: 'Čarovné dievča', timestamp: '2021-09-04' },
                { url: '/~xkubala/sivaStena/photos/kezmarok4.jpg', name: 'Kežmarok4', description: 'Krásne dievča', timestamp: '2021-08-29' }

            ];
        });


        const markerKk4 = new mapboxgl.Marker()
            .setLngLat([20.433929, 49.139530])
            .setPopup(popupKk4)
            .addTo(map);
        markerKk4.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/kezmarok1.jpg', name: 'Kežmarok1', description: 'Príroda z iného pohľadu', timestamp: '2019-10-02' },
                { url: '/~xkubala/sivaStena/photos/kezmarok2.jpg', name: 'Kežmarok2', description: 'Mystické dievča', timestamp: '2021-08-17' },
                { url: '/~xkubala/sivaStena/photos/kezmarok3.jpg', name: 'Kežmarok3', description: 'Čarovné dievča', timestamp: '2021-09-04' },
                { url: '/~xkubala/sivaStena/photos/kezmarok4.jpg', name: 'Kežmarok4', description: 'Krásne dievča', timestamp: '2021-08-29' }
            ];
            LightGallery
        });


        const markerStpleso = new mapboxgl.Marker()
            .setLngLat([20.057496, 49.121797])
            .setPopup(popupStpleso)
            .addTo(map);
        markerStpleso.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/Štrbske_Pleso1.jpg', name: 'Štrbské Pleso', description: 'Pohľad na pleso', timestamp: '2019-05-11' },
            ];
        });



        const markerPp = new mapboxgl.Marker()
            .setLngLat([20.280154, 49.056287])
            .setPopup(popupPp)
            .addTo(map);
        markerPp.getElement().addEventListener('click', () => {
            this.images = [
                { url: '/~xkubala/sivaStena/photos/poprad1.jpg', name: 'Poprad', description: 'Neidentifikovaný muž', timestamp: '2020-03-12' },
            ];
        });
    },
};

</script>

<style scoped>
div {
    margin-left: 10%;
    width: 80%;
    height: 450px;
}
</style>