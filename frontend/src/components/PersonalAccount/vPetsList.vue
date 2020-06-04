<template>
    <vCatGallery
        :animalsNumber="4"
        :isPaginationVisible="false"
    />
</template>

<script>
import vCatGallery from '../Catalog/vCatGallery'

export default {
    components:{
        vCatGallery
    },
    data(){
        return{

        }
    }
}
</script>