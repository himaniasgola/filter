<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Filters & Mixins</h1>
                <p>{{ text | toUpperCase | to-lowercase }}</p>
                <input v-model="filterText">
                <ul>
                    <li v-for="fruit in filteredFruits" :key="fruit">{{ fruit }}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                text: 'hello world',
                fruits: ['Apple','Mango','grapes','orange'],
                filterText: '',
            }
        },
        filters: {
            toUpperCase(value) {
                return value.toUpperCase();
            }
        },
        computed: {
            filteredFruits() {
                return this.fruits.filter((element) => {
                    return element.match(this.filterText);
                });
            }
        }
    }
</script>
