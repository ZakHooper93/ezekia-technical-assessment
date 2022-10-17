<template>
    <h2 class="blue-key">Core museum highlights</h2>
    <h2 class="orange-key">From our partners</h2>
    <div class="museum-highlight-grid">
        <li v-for="item in highlights" :key="item">
            <img
                :src="require(`/src/assets/highlights/${this.highlightImage(item.image)}.jpg`)"
                :class="imageOutlineColour(item.id)"
            />
            <img :src="require(`../assets/icons/${pageTheme}.png`)" class="theme-icon" />
            <h2 class="highlight-title">{{ item.name }}</h2>
            <div class="highlight-text">
                <p v-if="item.description">{{ item.description }}</p>
                <p v-if="item.info">{{ item.info }}</p>
                <p v-if="item.news?.title">{{ item.news.title }}</p>
                <p v-if="item.news?.date">{{ item.news.date }}</p>
                <a :href="item.quiz" v-if="item.quiz">Take our {{pageTheme}} quiz!</a>
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

.highlight-image-museum, .highlight-image-partner {
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
    text-align: left;
    margin-bottom: 5%;
}

.theme-icon {
    bottom: 100%;
    left: 0%;
    width: 50px;
    height: 50px;
    margin: 0;
}
.blue-key,
.orange-key {
    font-size: 12px;
    font-weight: 1000;
    text-align: left;
    margin-left: 5%;
}
.blue-key {
    color: blue;
}
.orange-key {
    color: orange;
}
</style>
