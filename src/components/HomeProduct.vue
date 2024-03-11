<template>
    <section class="home-products">

        <article class="shoe black">
            <RouterLink to="/product">
                <img src="@/assets/images/black.jpg" alt="black-sneakers" id="product3" class="product">
                <h4>Black</h4>
                <figure>
                    <p>$200</p>
                    <img src="@/assets/images/cart.png" alt="cart">
                </figure>
            </RouterLink>
        </article>

        <article class="shoe brown">
            <RouterLink to="/product">
                <img src="@/assets/images/brown.jpg" alt="black-sneakers" id="product3" class="product">
                <h4>Brown</h4>
                <figure>
                    <p>$367</p>
                    <img src="@/assets/images/cart.png" alt="cart">
                </figure>
            </RouterLink>
        </article>

        <article class="shoe white">
            <RouterLink to="/product">
                <img src="@/assets/images/white.jpg" alt="black-sneakers" id="product3" class="product">
                <h4>White</h4>
                <figure>
                    <p>$600</p>
                    <img src="@/assets/images/cart.png" alt="cart">
                </figure>
            </RouterLink>
        </article>

        <article class="shoe blue">
            <RouterLink to="/product">
                <img src="@/assets/images/blue.jpg" alt="blue-sneakers" id="product4" class="product">
                <h4>Blue</h4>
                <figure>
                    <p>$901</p>
                    <img src="@/assets/images/cart.png" alt="cart">
                </figure>
            </RouterLink>
        </article>

        <article class="shoe yellow">
            <RouterLink to="/product">
                <img src="@/assets/images/yellow.jpg" alt="blue-sneakers" id="product4" class="product">
                <h4>Yellow</h4>
                <figure>
                    <p>$1500</p>
                    <img src="@/assets/images/cart.png" alt="cart">
                </figure>
            </RouterLink>
        </article>

        <article class="shoe beige">
            <RouterLink to="/product">
                <img src="@/assets/images/beige.jpg" alt="blue-sneakers" id="product4" class="product">
                <h4>Beige</h4>
                <figure>
                    <p>$1734</p>
                    <img src="@/assets/images/cart.png" alt="cart">
                </figure>
            </RouterLink>
        </article>

    </section>
</template>

<script>
import '@/assets/styles/HomeProducts.scss';

export default {
    name: 'HomeProducts'
}
</script>

<style scoped>
@media (max-width: 768px) {
    .home-products {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 20px;
    }
}

@media (max-width: 768px) {
    .home-products {
        display: grid;
        grid-template-rows: repeat(2, 1fr);
        gap: 20px;
    }
}
</style>