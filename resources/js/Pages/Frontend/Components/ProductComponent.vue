<script setup>
defineProps({
    product: Object,
})

import { addToWishList, addToCart } from './Utils/CartWishManage';

</script>
<template>
    <div class="col">
        <div class="card card-product">
            <div class="card-body">

                <div class="text-center position-relative ">
                    <div class="top-0 position-absolute start-0">
                        <span class="badge bg-danger">{{ product.tag ? product.tag : ''
                            }}</span>
                    </div>
                    <Link :href="route('product.view', [product.category.slug, product.slug])">
                    <img :src="`/images/products/${JSON.parse(product.image)[0]}`" alt=""
                        class="mb-3 img-fluid"></Link>


                    <div class="card-product-action">
                        <a @click="$emit('selectedProduct', product)" href="#" class="btn-action" data-bs-toggle="modal"
                            data-bs-target="#productViewModal" data-id=""><i class="bi bi-eye" data-bs-toggle="tooltip"
                                data-bs-html="true" title="Quick View"></i></a>
                        <a @click="addToWishList(product.id)" class="btn-action" title="Wishlist"><i
                                class="bi bi-heart"></i></a>
                    </div>

                </div>
                <div class="mb-1 text-small"><a :href="route('category.view', product.category.slug)"
                        class="text-decoration-none text-muted"><small>{{ product.categoryName
                            }}</small></a>
                </div>
                <h2 class="fs-6"><a :href="route('product.view', [product.category.slug, product.slug])"
                        class="text-inherit text-decoration-none">{{ product.name }}</a></h2>
                <div>

                    <small class="text-warning"> <i class="bi bi-star-fill"></i>
                        <i class="bi bi-star-fill"></i>
                        <i class="bi bi-star-fill"></i>
                        <i class="bi bi-star-fill"></i>
                        <i class="bi bi-star-half"></i>
                    </small>
                </div>
                <div class="mt-3 d-flex justify-content-between align-items-center">
                    <div><span :show="product.sale_price" class="text-dark">{{ product.sale_price }}</span> <span
                            :class="product.sale_price ? 'text-decoration-line-through text-muted' : 'text-dark'">{{
                                product.price
                            }}</span>
                    </div>
                    <div><a @click="addToCart(product)" class="btn main-theme btn-sm">
                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24"
                                fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                stroke-linejoin="round" class="feather feather-plus">
                                <line x1="12" y1="5" x2="12" y2="19"></line>
                                <line x1="5" y1="12" x2="19" y2="12"></line>
                            </svg> Add
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
