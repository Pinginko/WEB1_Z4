<template>
    <div id="inField" v-show="showInput">
        <input type="text" id="textInput" v-model="inputValue" placeholder="Vyhľadaj podľa mesta !">
    </div>
    <div class="container-sm mx-auto d-block">
        <LightGallery id="boxGallery" v-if="images && images.length" :settings="{ speed: 500, plugins: plugins }"
            :onInit="onInit" :onBeforeSlide="onBeforeSlide">
            <a v-for="image in images" :key="image.name" :href="image.url" class="mx-auto"
                :data-sub-html="`<strong>${image.name}</strong><br>${image.description}<br>${image.timestamp}`">
                <img :alt="image.name" :src="image.url" />
            </a>
        </LightGallery>
    </div>
</template>
  
<script>
import { ref, defineComponent, onMounted, watch } from 'vue';
import LightGallery from 'lightgallery/vue';
import lgThumbnail from 'lightgallery/plugins/thumbnail';
import lgZoom from 'lightgallery/plugins/zoom';
import lgAutoplay from 'lightgallery/plugins/autoplay';
import 'lightgallery/scss/lightgallery.scss';
import 'lightgallery/css/lightgallery.css';
import 'lightgallery/css/lg-thumbnail.css';
import 'lightgallery/css/lg-zoom.css';
import 'lightgallery/css/lg-autoplay.css';




export default defineComponent({
    components: {
        LightGallery,
    },
    props: {
        showInput: {
            type: Boolean,
            default: true
        },
        images: {
            type: Array,
            default: () => []
        }
    },

    setup(props) {
        const plugins = ref([lgThumbnail, lgZoom, lgAutoplay]);
        const images = ref([]);
        const inputValue = ref("");
        const allImages = ref([]);
        const gallerry = ref();


        watch(() => props.images, (newImages) => {

            return new Promise((resolve) => {
                images.value = newImages;
                //images.value = allImages.value.filter(img => img.name.includes(inputValue.value) || img.description.includes(inputValue.value));
                resolve();
            })
                .then(() => {
                    gallerry.value.refresh();
                })
                .catch(error => {
                    console.error(error);
                });
        });


        const filterImages = () => {
            return new Promise((resolve, reject) => {
                images.value = allImages.value.filter(img => img.name.includes(inputValue.value) || img.description.includes(inputValue.value));
                resolve();
            })
                .then(() => {
                    gallerry.value.refresh();
                })
                .catch(error => {
                    console.error(error);
                });
        };

        watch(inputValue, () => {
            filterImages();
        });

        onMounted(() => {
            fetch('/~xkubala/sivaStena/images.json')
                .then(async response => await response.json())
                .then(data => {
                    allImages.value = data.images;
                    filterImages();
                })
                .catch(error => {
                    console.error(error);
                });
        });

        const onInit = (info) => {
            console.log('lightGallery has been initialized');
            gallerry.value = info.instance;
        };

        const onBeforeSlide = () => {
            console.log('calling before slide');
        };

        return {
            plugins,
            onInit,
            onBeforeSlide,
            images,
            inputValue,
        };
    },
});
</script>

<style scoped>
#inField {
    display: flex;
    justify-content: center;
}

input {

    border-radius: 7px;
    width: 23%;
    height: 37px;

}

#boxGallery {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

img {
    margin: .5em .5em;
    height: 12em;
    width: 12em;
    object-fit: cover;
    align-content: center;
}

div {
    margin-top: 1.5em;
}
</style>
