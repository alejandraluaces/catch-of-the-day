<template>
    <section class="page">
        <section class="content verticalCenter">
            <div class="container--shadow"></div>
            <section class="container--main">
                <p>The month is <strong>{{getMonth()}}</strong>.</p>
                <p>The hour is <strong>{{getHour()}}</strong>.</p>
                <p>The time of day is <strong>{{getAMPM()}}</strong>.</p>
                <li v-for="creature in creatures" v-if="getAMPM() == (creature.time) && filterMonth(creature.month)">
                    {{ creature.name }}
                </li>
            </section>
        </section>
        <footer>here are some things</footer>
    </section>
</template>


<script>

export default {
    name: 'item',

    computed: {
        date: function() {
            return new Date()
        }
    },

    data: function(){
        return {
            creatures: {
                "bitterling": {
                    "name": "Bitterling",
                    "cost": 900,
                    "month": [ 0, 1, 10, 11 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": [ "am", "pm" ],
                },
                "paleChub": {
                    "name": "Pale chub",
                    "cost": 200,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": "am",
                },
                "crucianCarp": {
                    "name": "Crucian carp",
                    "cost": 120,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 2,
                    "time": [ "am", "pm" ],
                },
                "dace": {
                    "name": "Dace",
                    "cost": 200,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 3,
                    "time": "pm",
                },
                "barbelSteed": {
                    "name": "Barbel steed",
                    "cost": 200,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 3,
                    "time": [ "am", "pm" ],
                },
                "carp": {
                    "name": "Carp",
                    "cost": 300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 4,
                    "time": [ "am", "pm" ],
                },
                "koi": {
                    "name": "Koi",
                    "cost": 4000,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "scarce",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 4,
                    "time": "pm",
                },
                "goldfish": {
                    "name": "Goldfish",
                    "cost": 1300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "scarce",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": [ "am", "pm" ],
                },
                "popeyedGoldfish": {
                    "name": "Popeyed goldfish",
                    "cost": 1300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "scarce",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": "am",
                },
                "killifish": {
                    "name": "Killifish",
                    "cost": 300,
                    "month": [ 3, 4, 5, 6, 7 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "pond",
                    "shadow size": 1,
                    "time": [ "am", "pm" ],
                },
                "crawfish": {
                    "name": "Crawfish",
                    "cost": 200,
                    "month": [ 3, 4, 5, 6, 7, 8 ],
                    "rarity": "common",
                    "type": "fish",
                    "location": "pond",
                    "shadow size": 2,
                    "time": [ "am", "pm" ],
                },
                "softshelledTurtle": {
                    "name": "Soft Shelled Turtle",
                    "cost": 3750,
                    "month": [ 7, 8 ],
                    "rarity": "rare",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 3,
                    "time": "pm",
                },
                "tadpole": {
                    "name": "Tadpole",
                    "cost": 1300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": [ "am", "pm" ],
                },
                "frog": {
                    "name": "Frog",
                    "cost": 1300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": [ "am", "pm" ],
                },
                "freshwaterGoby": {
                    "name": "Freshwater goby",
                    "cost": 1300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": "pm",
                },
                "loach": {
                    "name": "Loach",
                    "cost": 1300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": [ "am", "pm" ],
                },
                "catfish": {
                    "name": "Catfish",
                    "cost": 1300,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": "pm",
                },
                "eel": {
                    "name": "Eel",
                    "cost": 2000,
                    "month": [ 5, 6, 7, 8 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 0,
                    "time": "pm",
                },
                "giantSnakehead": {
                    "name": "Giant snakehead",
                    "cost": 5500,
                    "month": [ 5, 6, 7 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "lake",
                    "shadow size": 5,
                    "time": "am",
                },
                "bluegill": {
                    "name": "Bluegill",
                    "cost": 120,
                    "month": [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 2,
                    "time": "am",
                },
                "yellowPerch": {
                    "name": "Yellow perch",
                    "cost": 240,
                    "month": [ 0, 1, 2, 9, 10, 11 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 2,
                    "time": ["am", "pm"],
                },
                "blackBass": {
                    "name": "Black Bass",
                    "cost": 300,
                    "month": [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ],
                    "rarity": "common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 4,
                    "time": ["am", "pm"],
                },
                "pike": {
                    "name": "Pike",
                    "cost": 1800,
                    "month": [ 8, 9, 10, 11 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 5,
                    "time": "?",
                },
                "pondSmelt": {
                    "name": "Pond smelt",
                    "cost": 300,
                    "month": [ 0, 1, 11 ],
                    "rarity": "common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 2,
                    "time": ["am", "pm"],
                },
                "sweetfish": {
                    "name": "Sweetfish",
                    "cost": 900,
                    "month": [ 6, 7, 8, 9 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 3,
                    "time": ["am", "pm"],
                },
                "cherrySalmon": {
                    "name": "Cherry salmon",
                    "cost": 1000,
                    "month": [ 2, 3, 4, 5, 8, 9, 10 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 3,
                    "time": "?",
                },
                "char": {
                    "name": "Char",
                    "cost": 3800,
                    "month": [ 2, 3, 4, 5, 8, 9, 10 ],
                    "rarity": "uncommon",
                    "type": "fish",
                    "location": "waterfall",
                    "shadow size": 3,
                    "time": "?",
                },
                "rainbowTrout": {
                    "name": "Rainbow trout",
                    "cost": 800,
                    "month": [ 2, 3, 4, 5, 8, 9, 10 ],
                    "rarity": "fairly common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 4,
                    "time": "?",
                },
                "stringfish": {
                    "name": "Stringfish",
                    "cost": 15000,
                    "month": [ 0, 1, 11 ],
                    "rarity": "rare",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 6,
                    "time": "pm",
                },
                "salmon": {
                    "name": "Salmon",
                    "cost": 700,
                    "month": [ 8 ],
                    "rarity": "common",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 4,
                    "time": ["am", "pm"],
                },
                "kingSalmon": {
                    "name": "King salmon",
                    "cost": 1800,
                    "month": [ 8 ],
                    "rarity": "scarce",
                    "type": "fish",
                    "location": "waterfall",
                    "shadow size": 6,
                    "time": [ "am", "pm" ],
                },
                "mittenCrab": {
                    "name": "Mitten crab",
                    "cost": 2000,
                    "month": [ 8, 9, 10 ],
                    "rarity": "scarce",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 2,
                    "time": "pm",
                },
                "guppy": {
                    "name": "Guppy",
                    "cost": 1300,
                    "month": [ 5, 6, 7, 8 ],
                    "rarity": "scarce",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 1,
                    "time": "am",
                },
                "nibbleFish": {
                    "name": "Nibble fish",
                    "cost": 1500,
                    "month": [ 4, 5, 6, 7, 8 ],
                    "rarity": "scarce",
                    "type": "fish",
                    "location": "river",
                    "shadow size": 2,
                    "time": "am",
                },
            }
        }
    },

    methods: {

        getHour: function () {
            return this.date.getHours();
        },

        getAMPM: function() {
            if (this.getHour() > 16 || this.getHour() < 9 ) {
                return 'pm';
            } else {
                return 'am';
            }
        },

        getMonth: function() {
            return this.date.getMonth();
        },

        filterMonth: function (months) {
            if (months.includes(this.date.getMonth())) {
                return true;
            };
        },
    }
}

</script>


<style scoped>
    .page {
        display: flex;
        height: 100vh;
        flex-direction: column;
    }

    footer {
        background-color: black;
    }

    .content {
        order: -1;
        flex-direction: column;
        display: flex;
        flex: 1;
    }

    .verticalCenter {
        justify-content: center;
        align-items: center;
    }

    .container--main {
        width: 40%;
        position: absolute;
        background-color: #c0c0c0;
        z-index: 100;
    }

    .container--flex {
        display: flex;
    }

    .flex--row {
        flex-direction: row;
    }

    .container--shadow {
        border-left: 1px solid rebeccapurple;
        border-top: 1px solid rebeccapurple;
        z-index: -1;
        position: relative;
        top: -1em;
        left: -1em;
        width: 40%;
        background-color: lightpink;
        height: 160px;
    }

    .column {
        flex-direction: column;
    }
</style>
