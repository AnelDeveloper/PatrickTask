<template>



    <div class="Artikal">
        <div class="card" v-for="product in products" v-bind:key="product.id">
            <div class="embed-responsive embed-responsive-16by9">
                <img v-bind:src="product._source.image" />
            </div>

            <div class="card-body">
                <h5 class="card-title">{{ product._source.name }}</h5>


                <p class="card-text font-italic">
                    {{ product._source.price }}$
                    {{ product._source.image }}

                </p>

            </div>
        </div>
    </div>
</template>

<script>




export default {
    name: 'ArtikalComp',
    data() {
        return {
            products: [

            ]
        }

    },

    mounted() {
        try {
            fetch('https://www.roastmarket.de/api/catalog/vue_storefront_catalog/product/_search?')
                .then(response => response.json())
                .then(response => (this.products = response.hits.hits, console.log(response.hits.hits)))



        } catch (e) {
            console.error(e);

        }



    },







}

</script>



<style>
.Artikal {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

}

.picture {
    font-size: 16px;
    font-family: Arial, sans-serif;
    font-weight: 400;
    line-height: 1.5;
    text-align: center;
    color: #211714;
    -webkit-tap-highlight-color: transparent;
    box-sizing: border-box;
    padding: 0;
    max-width: 100%;
    animation: images-lazy-loading;
    animation-duration: .3s;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    width: 100%;
}

.card {
    display: flex;
    flex-direction: column;
    align-items: center;
    font-size: 16px;
    font-family: 'Arial', sans-serif;
    font-weight: 400;
    line-height: 1.5;
    height: 400px;
    box-sizing: border-box;
    padding: 10px;

    margin-top: 50px;
    padding: 0;
    left: 20px;
    text-align: center;
    width: 45%;
    position: relative;
    box-shadow: 0 0 10px 0 rgba(26, 27, 27, 0.1);
    padding-bottom: 55px;
    margin-bottom: 20px;

}

.embed-responsive .card-img-top {
    object-fit: cover;
}

a {
    text-decoration: none;
}

.card-title {
    color: #484848;
    font-size: 1.1rem;
    font-weight: 400;

}

.card-title:hover {
    font-weight: bold;
}

.card-text {
    font-size: 0.9rem;
}
</style>