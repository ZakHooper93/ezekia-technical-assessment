<template>
    <h2 class="key key--blue">Blue - Central museum highlights</h2>
    <h2 class="key key--orange">Orange - From our wonderful partners</h2>
    <div class="museum-highlight-grid">
        <li v-for="item in highlights" :key="item">
            <img
                :src="require(`/src/assets/highlights/${this.highlightImage(item.image)}.jpg`)"
                :class="imageOutlineColour(item.id)"
            />
            <img 
                :src="require(`../assets/icons/${pageTheme}.png`)" 
                class="theme-icon" 
            />
            <h2 class="highlight-title">{{ item.name }}</h2>
            <div class="highlight-text">
                <p v-if="item.description">{{ item.description }}</p>
                <p v-if="item.info">{{ item.info }}</p>
                <p v-if="item.news?.title">{{ item.news.title }}</p>
                <p v-if="item.news?.date">{{ item.news.date }}</p>
                <a :href="item.quiz" v-if="item.quiz">Take our {{ pageTheme }} quiz!</a>
            </div>
        </li>
    </div>
</template>

<script>
export default {
    name: 'MuseumHighlight',
    props: {
        highlights: {
            type: Object
        },
        pageTheme: {
            type: String
        }
    },

    methods: {
        highlightImage(highlightImage) {
            return highlightImage ? highlightImage : `${this.pageTheme}Placeholder`;
        },
        imageOutlineColour(itemId) {
            return itemId ? 'highlight-image-museum' : 'highlight-image-partner';
        },
        themeIcon(theme) {
            return `../assets/icons/${theme}.jpg`;
        }
    }
};
</script>

<style lang="scss" scoped>
.museum-highlight-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
}

.museum-highlight-grid li {
    width: 1fr;
    height: 1fr;
    margin: 50px;
    list-style: none;
}

.highlight-image-museum,
.highlight-image-partner {
    width: 400px;
    height: 400px;
}

.highlight-image-museum {
    box-shadow: 5px 5px 10px blue;
}

.highlight-image-partner {
    box-shadow: 5px 5px 10px orange;
}

.highlight-title {
    text-decoration: underline;
}

.highlight-text {
    vertical-align: top;
    display: inline-block;
    text-align: center;
    width: 400px;
    margin-bottom: 5%;
}

.theme-icon {
    position: absolute;
    top: 1;
    left: 1;
    width: 100px;
    height: 100px;
    margin: 0;
}

.key {
    font-size: 12px;
    font-weight: 1000;
    text-align: left;
    margin-left: 5%;
}

.key--blue {
    color: blue;
}

.key--orange {
    color: orange;
}
</style>
