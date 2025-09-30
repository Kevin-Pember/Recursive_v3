<script lang="ts">
  export let target: any;
  export let gridLayout: string = `"sin one two three plus"
                             "cos four five six minus"
                             "tan seven eight nine multi"
                             "ln pow zero sqrt divide"
                             "inv . . . ."`;
  //'"sin 1 2 3 +""cos 4 5 6 -""tan 7 8 9 ×""ln pow 0 sqrt ÷""inv"'
  let keyInput = (type: string, key: any) => {
    if (type == "insert") {
      return () => {
        target.executeCommand(["insert", key, { selectionMode: "after" }]);
        target.executeCommand(["moveToNextChar"]);
      };
    } else {
      return key;
    }
  };
  const keyTemplates = {
    sin: {
      c: keyInput("insert", "sin("),
      content: "sin",
      generic: "sin",
    },
    "1": {
      c: keyInput("insert", "1"),
      content: "1",
      generic: "one",
    },
    "2": {
      c: keyInput("insert", "2"),
      content: "2",
      generic: "two",
    },
    "3": {
      c: keyInput("insert", "3"),
      content: "3",
      generic: "three",
    },
    "+": {
      c: keyInput("insert", "+"),
      content: "+",
      generic: "plus",
    },
    cos: {
      c: keyInput("insert", "cos("),
      content: "cos",
      generic: "cos",
    },
  };
</script>

<div id="keypad" style="visibility: inherit;">
  <arrow-icon id="arrowIcon" class="arrows imgDivClass iconType" direction="up"
  ></arrow-icon>
  <div id="mainCacGrid">
    <div id="gridBackDrop" class="paneType"></div>
    <button
      class="gridButton keypadButton"
      id="num1"
      name="1"
      style="grid-area: num1;">1</button
    >
    <button
      class="gridButton keypadButton"
      id="num2"
      name="2"
      style="grid-area: num2;">2</button
    >
    <button
      class="gridButton keypadButton"
      id="num3"
      name="3"
      style="grid-area: num3;">3</button
    >
    <button
      id="moreFunctionsButton"
      class="keypadButton gridButton fI"
      style="grid-area: moreFuncBut;"
      tabindex="-1">𝑓</button
    >
    <button class="gridButton keypadButton" id="num4" style="grid-area: num4;"
      >4</button
    >
    <button class="gridButton keypadButton" id="num5" style="grid-area: num5;"
      >5</button
    >
    <button class="gridButton keypadButton" id="num6" style="grid-area: num6;"
      >6</button
    >
    <button
      class="gridButton keypadButton fI"
      id="backspace"
      style="grid-area: backspace;display: grid;justify-content: center;align-content: center;"
    >
      <svg
        id="backspcaeIcon"
        style="height: 20px; width: 40px;isolation:isolate"
        viewBox="0 0 1080 540"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect width="1080" height="540" fill-opacity="0" />
        <path
          class="text"
          d="m657.21 270-147.56 147.13 37.394 37.284 147.56-147.13 147.56 147.13 37.395-37.284-147.56-147.13 147.56-147.13-37.395-37.284-147.56 147.13-147.56-147.13-37.394 37.284 147.56 147.13zm-231.69-247.29v-1.106l-403.92 248.4 403.92 248.4v-1.106c14.803 14.068 34.815 22.706 56.829 22.706h515.12c45.548 0 82.527-36.979 82.527-82.527v-374.95c0-45.548-36.979-82.527-82.527-82.527h-515.12c-22.014 0-42.026 8.638-56.829 22.706z"
          fill-rule="evenodd"
        />
      </svg>
    </button>
    <button class="gridButton keypadButton" id="num7" style="grid-area: num7;"
      >7</button
    >
    <button class="gridButton keypadButton" id="num8" style="grid-area: num8;"
      >8</button
    >
    <button class="gridButton keypadButton" id="num9" style="grid-area: num9;"
      >9</button
    >
    <button
      class="gridButton keypadButton fI"
      id="plus"
      style="grid-area: plus;">+</button
    >
    <button class="gridButton keypadButton" id="piButton" style="grid-area: pi;"
      >π</button
    >
    <button class="gridButton keypadButton" id="num0" style="grid-area: num0;"
      >0</button
    >
    <button
      class="gridButton keypadButton"
      id="pointButton"
      style="grid-area: point;">.</button
    >
    <button
      class="gridButton keypadButton fI"
      id="minus"
      style="grid-area: minus;">-</button
    >
    <button
      class="gridButton keypadButton fI"
      id="percent"
      style="grid-area: percent;">%</button
    >
    <button
      class="gridButton keypadButton fI"
      id="pars"
      style="grid-area: pars;">( )</button
    >
    <button class="gridButton keypadButton fI" id="pow" style="grid-area: pow;"
      >^</button
    >
    <button
      class="gridButton keypadButton fI"
      id="multiplication"
      style="grid-area: multiplication;">×</button
    >
    <button
      class="gridButton keypadButton fI"
      id="enter"
      style="grid-area: enter;">enter</button
    >
    <button
      class="gridButton keypadButton fI"
      id="pow2"
      style="grid-area: pow2;">x²</button
    >
    <button
      class="gridButton keypadButton fI"
      id="sqrt"
      style="grid-area: sqrt;">√x</button
    >
    <button
      class="gridButton keypadButton fI"
      id="division"
      style="grid-area: division;">÷</button
    >
  </div>
  <div id="extraFuncPopUp">
    <div id="customFuncDisplayPopup" class="paneType" data-element="popup">
      <plus-icon id="addIconPopup" class="standaloneButtons iconType" test="sd"
      ></plus-icon>
      <minus-icon
        id="minusIconPopup"
        class="standaloneButtons iconType"
        animated="true"
      ></minus-icon>
      <div id="custFuncGridPopup"></div>
    </div>
    <div class="customFuncDisplayBackgroundPopup w-full" ></div>

    <div id="extraFuncPopUpGrid">
      <button
        class="gridButton keypadButton fI"
        id="helpPopup"
        style="grid-area: help;display: grid;justify-content: center;align-content: center;"
      >
        <svg
          class="helpIcon imgDivClass"
          style="height: 30px;isolation:isolate"
          viewBox="0 0 45 45"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            class="text"
            d="m4 22.5c0-10.21 8.29-18.5 18.5-18.5s18.5 8.29 18.5 18.5-8.29 18.5-18.5 18.5-18.5-8.29-18.5-18.5zm20.474 6.395h-4.095q-0.016-0.883-0.016-1.076 0-1.991 0.659-3.276 0.658-1.284 2.633-2.89 1.976-1.606 2.361-2.104 0.594-0.787 0.594-1.734 0-1.317-1.052-2.257-1.052-0.939-2.834-0.939-1.718 0-2.875 0.979-1.156 0.98-1.59 2.987l-4.143-0.513q0.177-2.875 2.449-4.882 2.273-2.008 5.966-2.008 3.886 0 6.183 2.032 2.296 2.031 2.296 4.729 0 1.494-0.843 2.826-0.843 1.333-3.605 3.63-1.429 1.188-1.775 1.911-0.345 0.722-0.313 2.585zm0.418 6.071h-4.513v-4.513h4.513v4.513z"
            fill-rule="evenodd"
          />
        </svg>
      </button>
      <button
        class="gridButton keypadButton"
        id="deciToFracPopup"
        style="grid-area: dToF;">d→f</button
      >
      <button
        class="gridButton keypadButton"
        id="keyboardPopup"
        style="grid-area: vars;">xyz</button
      >
      <button
        class="gridButton keypadButton"
        id="acPopup"
        style="grid-area: ac;">ac</button
      >
      <button
        class="gridButton keypadButton"
        id="log10Popup"
        style="grid-area: log;">log<sub>10</sub></button
      >
      <button
        class="gridButton keypadButton"
        id="lnPopup"
        style="grid-area: ln;">ln</button
      >
      <button class="gridButton keypadButton" id="ePopup" style="grid-area: e;"
        >e</button
      >
      <button
        class="gridButton keypadButton fI"
        id="factorialPopup"
        style="grid-area: fact;">n!</button
      >
      <button
        class="gridButton keypadButton fI"
        id="degPopup"
        style="grid-area: deg;">deg</button
      >
      <button
        class="gridButton keypadButton fI"
        id="arcPopup"
        style="grid-area: arc;">arc</button
      >
      <button
        class="gridButton keypadButton fI"
        id="invPopup"
        style="grid-area: inv;">inv</button
      >
      <button
        class="gridButton keypadButton fI"
        id="absPopup"
        style="grid-area: abs;">||</button
      >
      <button
        class="trigButton keypadButton gridButton fI"
        id="sinPopup"
        style="grid-area: sin;">sin</button
      >
      <button
        class="trigButton keypadButton gridButton fI"
        id="cosPopup"
        style="grid-area: cos;">cos</button
      >
      <button
        class="trigButton keypadButton gridButton fI"
        id="tanPopup"
        style="grid-area: tan;">tan</button
      >
      <button
        class="gridButton keypadButton fI"
        id="modPopup"
        style="grid-area: mod;">mod</button
      >
    </div>
  </div>
</div>

<style>
  #extraFuncPopUp {
    height: 100%;
    width: 100%;
    top: 100%;
    display: block;
    position: absolute;
    z-index: 1;
    visibility: inherit;
  }
  #keypad {
    height: 100%;
    width: 100%;
    overflow: hidden;
    background-color: var(--primary);
  }
  #mainCacGrid {
    position: absolute;
    width: 100%;
    height: 100%;
    display: grid;
    grid-gap: 0px 0px;
    margin: 0px;
    grid-template-columns: 25% 25% 25% 25%;
    grid-template-rows: 16.6666% 16.6666% 16.6666% 16.6666% 16.6666% 16.6666%;
    background-color: #00000000;
    grid-template-areas:
      "num1 num2 num3 moreFuncBut"
      "num4 num5 num6 backspace"
      "num7 num8 num9 plus"
      "pi num0 point minus"
      "percent pars pow multiplication"
      "enter pow2 sqrt division";
  }
  #gridBackDrop {
    position: absolute;
    width: 75%;
    height: 66.6666%;
    top: 0px;
    left: 0px;
    z-index: 0;
    background-color: var(--accent);
  }

  #moreFunctionsButton {
    height: 100%;
    width: 100%;
    font-size: 15px;
    color: var(--text);
    text-align: center;
    border-style: none;
    position: relative;
    grid-area: moreFuncBut;
  }

  #arrowIcon {
    visibility: inherit;
    top: 10px;
    transition: transform 0.125s;
    right: 10px;
    font-size: 15px;
    text-align: center;
    stroke: transparent;
    stroke-width: 0px;
    background-color: #00000000;
    position: absolute;
    z-index: 2;
    height: 35px;
    pointer-events: all;
    background-color: var(--secondary);
  }

  #backspace {
    flex-shrink: 0;
    grid-area: backspace;
  }

  #backspaceDiv {
    display: flex;
  }
  #customFuncDisplayPopup {
    height: 33.3333%;
    width: 100%;
    top: 0;
    background-color: var(--accent);
    position: absolute;
    z-index: 1;
    overflow-x: auto;
  }
  #custFuncGridPopup {
    position: absolute;
    left: 0;
    width: 100%;
    top: 50px;
    padding: 0px 5px 0 5px;
    bottom: 5px;
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: 50%;
    overflow-x: auto;
    overflow-y: hidden;
  }
  .customButton {
    margin-left: 5px;
    position: relative;
    background-color: var(--secondary);
    color: var(--text);
    width: calc(100% - 10px);
    z-index: 2;
    flex-shrink: 0;
    top: 2.5%;
    height: 95%;
  }
  #extraFuncPopUpGrid {
    position: absolute;
    height: 66.6666%;
    width: 100%;
    top: 33.3333%;
    display: grid;
    grid-gap: 0px 0px;
    margin: 0px;
    grid-template-columns: 25% 25% 25% 25%;
    grid-template-rows: 25% 25% 25% 25%;
    background-color: #00000000;
    grid-template-areas:
      "help dToF vars ac"
      "log ln e fact"
      "deg arc inv abs"
      "sin cos tan mod";
  }
  .keypadButton {
    overflow: hidden;
    text-align: center;
  }

  .keypadButton:after {
    content: "";
    background: transparent;
    position: absolute;
    display: block;
    top: 2.5px;
    left: 2.5px;
    border-radius: 25px;
    width: calc(100% - 5px);
    height: calc(100% - 5px);
    opacity: 0;
    z-index: 1;
    transition: all 0.5s ease;
  }

  .keypadButton:active:after {
    transform: scale(0.5);
    background: var(--text);
    border-radius: 50%;
    margin-left: 25%;
    width: unset;
    aspect-ratio: 1/1;
    opacity: 0.2;
    transition: 0s;
  }
  @font-face {
    font-family: ubuntu;
    src: url(../fontAssets/Roboto-Regular.ttf);
  }

  @font-face {
    font-family: ubuntu;
    src: url(../fontAssets/Roboto-Bold.ttf);
    font-weight: bold;
  }

  :root {
    --secondary: #3d3d3d;
    --accent: #15ad6e;
    --primary: #1b1b1b;
    --text: #48fea6;
    --translucent: #00000033;
    --semi-transparent: #000000c5;
    --neutralColor: #80808080;
  }

  body {
    background: var(--secondary);
    overflow: hidden;
    position: absolute;
    left: 0;
    right: 0;
  }

  .imgDivClass {
    aspect-ratio: 1 / 1;
  }

  button:focus {
    outline: none;
  }

  .fI {
    background-color: var(--secondary);
  }

  .numsbutton {
    height: 100%;
    width: 100%;
    font-size: 20px;
    color: var(--text);
    background-color: var(--accent);
    text-align: center;
    border-style: none;
  }

  .numsbutton:focus {
    outline: none;
    box-shadow: none;
  }
  .gridButton {
    height: 100%;
    width: 100%;
    font-size: 20px;
    color: var(--text);
    background-color: transparent;
    text-align: center;
    border-style: none;
    position: absolute;
  }
  .funcbutton {
    height: 100%;
    width: 100%;
    font-size: 20px;
    color: var(--text);
    background-color: var(--primary);
    text-align: center;
    border-style: none;
  }

  button:focus {
    outline: none;
    box-shadow: none;
  }

  .keypadButton {
    overflow: hidden;
    text-align: center;
  }

  .keypadButton:after {
    content: "";
    background: transparent;
    position: absolute;
    display: block;
    top: 2.5px;
    left: 2.5px;
    border-radius: 25px;
    width: calc(100% - 5px);
    height: calc(100% - 5px);
    opacity: 0;
    z-index: 1;
    transition: all 0.5s ease;
  }

  .keypadButton:active:after {
    transform: scale(0.5);
    background: var(--text);
    border-radius: 50%;
    margin-left: 25%;
    width: unset;
    aspect-ratio: 1/1;
    opacity: 0.2;
    transition: 0s;
  }

  .trigButton {
    height: 100%;
    width: 100%;
    font-size: 20px;
    color: var(--text);
    background-color: var(--primary);
    text-align: center;
    border-style: none;
  }
  .standaloneButtons {
    height: 35px;
    width: 35px;
    top: 10px;
    margin-left: 10px;
  }
  #addIconPopup {
    background-color: transparent;
    position: absolute;
    background-color: var(--secondary);
  }

  #minusIconPopup {
    background-color: transparent;
    margin-left: 50px;
    position: absolute;
    background-color: var(--secondary);
  }

  .customFuncDisplayBackgroundPopup {
    height: 44.4444%;
    left: 0;
    top: 11.1111%;
    background-color: var(--primary);
    position: relative;
    z-index: -1;
  }

  #extraFuncPopUpGrid {
    position: absolute;
    height: 66.6666%;
    width: 100%;
    top: 33.3333%;
    display: grid;
    grid-gap: 0px 0px;
    margin: 0px;
    grid-template-columns: 25% 25% 25% 25%;
    grid-template-rows: 25% 25% 25% 25%;
    background-color: var(--primary);
    grid-template-areas:
      "help dToF vars ac"
      "log ln e fact"
      "deg arc inv abs"
      "sin cos tan mod";
  }
</style>
