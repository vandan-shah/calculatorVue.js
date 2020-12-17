<template>
    <div class="formstyle">
        <div class="row">
            <div class="calculator">

                <div class="input">{{ current || '0' }}</div><br><br>

                <div class="row1">
                    <button @click="append('1')" data-type="number" class="num 1">1</button>
                    <button @click="append('2')" data-type="number" class="num 2">2</button>
                    <button @click="append('3')" data-type="number" class="num 3">3</button>
                    <button @click="divide" data-type="operator" data-key="divide" class="operator divide">&#247;</button>
                    <br>


                    <button @click="append('4')" data-type="number" class="num 4">4</button>
                    <button @click="append('5')" data-type="number" class="num 5">5</button>
                    <button @click="append('6')" data-type="number" class="num 6">6</button>
                    <button @click="times" data-type="operator" data-key="multiply" class="operator multiply">&times;</button>
                    <br>


                    <button @click="append('7')" data-type="number" class="num 7">7</button>
                    <button @click="append('8')" data-type="number" class="num 8">8</button>
                    <button @click="append('9')" data-type="number" class="num 9">9</button>
                    <button @click="minus" data-type="operator" data-key="subtract" class="operator subtract">-</button>
                    <br>


                    <button @click="clear" data-type="clear" class="clear">CE</button>
                    <button @click="append('0')" data-type="number" class="num 0">0</button>
                    <button @click="equal" data-type="equal" class="num equal">=</button>
                    <button @click="add" data-type="operator" data-key="add" class="operator add">+</button>
                    <br>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            previous: null,
            current: '',
            operator: null,
            operatorClicked: false
        }
    },
    methods: {
        setPrevious() {
            this.previous = this.current
            this.operatorClicked = true
        },
        append(number) {
            if (this.operatorClicked) {
                this.current = '',
                this.operatorClicked = false
            }
            this.current = `${this.current}${number}`
        },
        divide() {
            this.operator = (a, b) => a / b
            this.setPrevious()
        },
        times() {
            this.operator = (a, b) => a * b
            this.setPrevious()
        },
        minus() {
            this.operator = (a, b) => a - b
            this.setPrevious()
        },
        add() {
            this.operator = (a, b) => a + b
            this.setPrevious()
        },
        clear() {
            this.current = ''
        },
        equal() {
            this.current = `${this.operator(parseFloat(this.previous), parseFloat(this.current))}`
            this.previous = null
        }
    }
}
</script>

<style>

</style>