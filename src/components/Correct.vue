<template>
    <div id="correct">
        <div id="question">
            <h4>What's 27 - 24?</h4>
        </div>
        <div id="answers">
            <button>2</button>
            <button>3</button>
            <button>4</button>
            <button>5</button>
        </div>
    </div>
</template>

<style scoped>
h4 {
    margin: 0;
}

#question {
    background-color: #EEEEEE;
    text-align: center;
    border: 1px solid darkgray;
    height: 30px;
    line-height: 30px;
}

#answers {
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
}

#correct {
    border: 1px solid gray;
    width: 40%;
    margin: 0 auto;
}

button {
    width: 25%;
    margin: 5% 12.5%;
    background-color: lightskyblue;
    border: 1px solid darkgray;
    border-radius: 8px;
    height: 30px;
    color: white;
    font-weight: 600;
    font-size: 16px;
    cursor: pointer;
}

button:focus {
    outline: none;
}
</style>
