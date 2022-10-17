<template>
    <div class="space-page">
        <h1 class="space-page__title">Space</h1>
        <museum-highlight 
        :highlights="dateSortedSpaceHighlights" 
        pageTheme="space" 
        />
    </div>
</template>

<script>
import _ from 'lodash';
import MuseumHighlight from './MuseumHighlight.vue';

export default {
    name: 'SpacePage',
    components: {
        MuseumHighlight
    },

    data() {
        return {
            spaceHighlights: [
                {
                    date: '2020-04-20 12:20:00',
                    description:
                        'Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.',
                    id: 1,
                    image: '',
                    name: 'Asteroids'
                },
                {
                    date: '2020-05-20 15:50:00',
                    description:
                        'A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.',
                    id: 9,
                    image: '',
                    name: 'Comets'
                },
                {
                    date: '2020-05-01 9:22:00',
                    description:
                        'The term planet is ancient, with ties to history, astrology, science, mythology, and religion.',
                    id: 7,
                    image: '',
                    name: 'Planets',
                    news: {
                        date: '2020-08-18 18:00:00',
                        title: 'Attend our talk about Jupiter with Dr. Hogarth'
                    },
                    quiz: 'https://planetquiz.space'
                },
                {
                    date: '2020-07-05 4:10:00',
                    description:
                        'A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.',
                    id: 12,
                    image: '',
                    name: 'Meteor showers',
                    news: {
                        title: 'The Lyrids will peak at on April 21-22 2021, at night'
                    }
                }
            ],
            spacePartners: {
                observatory: {
                    createdAt: '2020-06-01 11:45:00',
                    info: 'The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.',
                    image: '',
                    name: 'Mauna Kea Observatories'
                }
            }
        };
    },

    computed: {
        dateSortedSpaceHighlights() {
            return _.sortBy(this.mergedHighlights(), [
                function (o) {
                    return o.user;
                }
            ]).reverse();
        }
    },

    methods: {
        mergedHighlights() {
            return new Array(...this.spaceHighlights, ...Object.values(this.spacePartners))
        }
    }
};
</script>

<style lang="scss" scoped>
.space-page {
    &__title {
        font-family: sans-serif;
        color: #2c3791;
        font-size: 36px;
        font-weight: 300;
        text-align: left;
        margin-left: 5%;
        text-decoration: underline;
    }
}
</style>
