<script lang="ts">
    
    export let target: any;
    export let gridLayout: string = `"sin one two three plus"
                             "cos four five six minus"
                             "tan seven eight nine multi"
                             "ln pow zero sqrt divide"
                             "inv . . . ."`
    //'"sin 1 2 3 +""cos 4 5 6 -""tan 7 8 9 ×""ln pow 0 sqrt ÷""inv"'
    let keyInput = (type:string,key:any) => {
        if("insert"){
            return  () => {target.executeCommand(["insert", key, {selectionMode: "after"}]); target.executeCommand(["moveToNextChar"])}
        }else{
            return key
        }
    }
    const keyTemplates = {
        "sin":{
            "c":keyInput("insert","sin("),
            "content": "sin",
            "generic": "sin"
        },
        "1":{
            "c":keyInput("insert","1"),
            "content": "1",
            "generic": "one"
        },
        "2":{
            "c":keyInput("insert","2"),
            "content": "2",
            "generic": "two"
        },
        "3":{
            "c":keyInput("insert","3"),
            "content": "3",
            "generic": "three"
        },
        "+":{
            "c":keyInput("insert","+"),
            "content": "+",
            "generic": "plus"
        },
        "cos":{
            "c":keyInput("insert","cos("),
            "content": "cos",
            "generic": "cos"
        }

    }
</script>
<div id="keypad-layout" style='--layout:{gridLayout};' class="bg-[var(--secondary)]">
    <button style="grid-area: sin;" on:click={keyInput("insert","sin(")}>sin</button>
    <button style="grid-area: one;" on:click={keyInput("insert","1")}>1</button>
    <button style="grid-area: two;" on:click={keyInput("insert","2")}>2</button>
    <button style="grid-area: three;" on:click={keyInput("insert","3")}>3</button>
    <button style="grid-area: plus;" on:click={keyInput("insert","+")}>+</button>
    <button style="grid-area: cos;" on:click={keyInput("insert","cos(")}>cos</button>
    <button style="grid-area: four;" on:click={keyInput("insert","4")}>4</button>
    <button style="grid-area: five;" on:click={keyInput("insert","5")}>5</button>
    <button style="grid-area: six;" on:click={keyInput("insert","6")}>6</button>
    <button style="grid-area: minus;" on:click={keyInput("insert","-")}>-</button>
    <button style="grid-area: tan;" on:click={keyInput("insert","tan(")}>tan</button>
    <button style="grid-area: seven;" on:click={keyInput("insert","7")}>7</button>
    <button style="grid-area: eight;" on:click={keyInput("insert","8")}>8</button>
    <button style="grid-area: nine;" on:click={keyInput("insert","9")}>9</button>
    <button style="grid-area: multi;" on:click={keyInput("insert","*")}>*</button>
    <button style="grid-area: ln;" on:click={keyInput("insert","ln(")}>ln</button>
    <button style="grid-area: pow;" on:click={keyInput("insert","^")}>^</button>
    <button style="grid-area: zero;" on:click={keyInput("insert","0")}>0</button>
    <button style="grid-area: divide;" on:click={keyInput("insert","÷")}>÷</button>
    <button style="grid-area: inv;" on:click={keyInput("insert","ln(")}>inv</button>
    <button style="grid-area: indsv;" on:click={keyInput("insert","ln(")}>test</button>
    
    
</div>
<style>
    #keypad-layout{
        overflow: hidden;
        max-width: 400px;
        height: 400px;
        display: grid;
        grid-template-columns: 20% 20% 20% 20% 20%;
        grid-gap: 0px 0px;
        grid-template-rows: 20% 20% 20% 20% 20%;
        grid-template-areas: var(--layout);
    }
    #keypad_layout:nth-child(2n+1) {
        background-color: red;
    }
</style>
