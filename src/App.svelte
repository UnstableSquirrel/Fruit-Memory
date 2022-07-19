<script>

  let Fruits = [
    // {
    //   "Name" : "Apple",
    //   "Nr" : "0",
    //   "Src" : "https://gooey-companion.vercel.app/apple.png"
    // },
    {
      "Name" : "Orange",
      "Nr" : "1",
      "Src" : "https://gooey-companion.vercel.app/orange.png",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Banana",
      "Nr" : "2",
      "Src" : "https://gooey-companion.vercel.app/banana.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Strawberry",
      "Nr" : "3",
      "Src" : "https://gooey-companion.vercel.app/strawberry.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Cherry",
      "Nr" : "4",
      "Src" : "https://gooey-companion.vercel.app/cherry.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Pineapple",
      "Nr" : "5",
      "Src" : "https://gooey-companion.vercel.app/pineapple.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Coconut",
      "Nr" : "6",
      "Src" : "https://gooey-companion.vercel.app/coconut.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Foxtail",
      "Nr" : "7",
      "Src" : "https://gooey-companion.vercel.app/foxtail.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Pancake",
      "Nr" : "8",
      "Src" : "https://gooey-companion.vercel.app/pancake.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Devil",
      "Nr" : "9",
      "Src" : "https://gooey-companion.vercel.app/devil.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Moondrop",
      "Nr" : "10",
      "Src" : "https://gooey-companion.vercel.app/moondrop.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Orange2",
      "Nr" : "1",
      "Src" : "https://gooey-companion.vercel.app/orange.png",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Banana2",
      "Nr" : "2",
      "Src" : "https://gooey-companion.vercel.app/banana.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Strawberry2",
      "Nr" : "3",
      "Src" : "https://gooey-companion.vercel.app/strawberry.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Cherry2",
      "Nr" : "4",
      "Src" : "https://gooey-companion.vercel.app/cherry.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Pineapple2",
      "Nr" : "5",
      "Src" : "https://gooey-companion.vercel.app/pineapple.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Coconut2",
      "Nr" : "6",
      "Src" : "https://gooey-companion.vercel.app/coconut.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Foxtail2",
      "Nr" : "7",
      "Src" : "https://gooey-companion.vercel.app/foxtail.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Pancake2",
      "Nr" : "8",
      "Src" : "https://gooey-companion.vercel.app/pancake.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Devil2",
      "Nr" : "9",
      "Src" : "https://gooey-companion.vercel.app/devil.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
    {
      "Name" : "Moondrop2",
      "Nr" : "10",
      "Src" : "https://gooey-companion.vercel.app/moondrop.jpg",
      "Class" : "",
      "Picked" : "False",
      "Class2" : "",
    },
  ]





  function shuffle(array) {
  let currentIndex = array.length,  randomIndex

  while (currentIndex != 0) {

    randomIndex = Math.floor(Math.random() * currentIndex)
    currentIndex--

    [array[currentIndex], array[randomIndex]] = [
      array[randomIndex], array[currentIndex]]
  }

  return array
}





let arr = []
arr = shuffle(Fruits)
let selected = []
let flipsCount = 0
let pairsCount = 0
let seconds = 0





function check() {

  if ((arr.filter(i => i.Picked == "true")).length <= 1) {
    let pos = arr.findIndex(i => i.Name == selected[0])
    flipsCount += 1
    arr[pos].Picked = "true"
    arr[pos].Class = "turn"
  }

  if (flipsCount == 1) { 
      setInterval(startCountdown, 1000)
      function startCountdown() {
        if(pairsCount < 10) {
          seconds = seconds + 1
        }
      }
  }

  selected = []

  checkForPair()
}

function checkForPair() {
  if ((arr.filter(i => i.Picked == "true")).length == 2) {
    const t1 = setTimeout(turn1, 500)
    function turn1() {
      let pos1 = arr.findIndex(i => i.Picked == "true")
      // @ts-ignore
      // let pos2 = arr.findLastIndex(i => i.Picked == "true")
      let a = arr.map((item) => item.Picked)
      let pos2 = a.lastIndexOf("true")
      // console.log(pos1, pos2)

      if (arr[pos1].Nr == arr[pos2].Nr) {
        pairsCount += 1
        arr[pos1].Picked = "false"
        arr[pos1].Class = "turn"
        arr[pos2].Picked = "false"
        arr[pos2].Class = "turn"
        arr[pos1].Class2 = "selected"
        arr[pos2].Class2 = "selected"
      }
      if (arr[pos1].Nr != arr[pos2].Nr) {
        arr[pos1].Picked = "false"
        arr[pos1].Class = ""
        arr[pos2].Picked = "false"
        arr[pos2].Class = ""
      }
    }
  }
}




function rl() {
  location.reload()
}







</script>

<main>
  <h1>Fruit Memory</h1>

  {#if pairsCount == 10}
  <div class="modal show-modal">
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="confetti"></div>
    <div class="modal-content">
        <!-- <span class="close-button">&times;</span> -->
        <h1>You Won</h1>
        <p>With <span>{flipsCount}</span> Flips</p>
        <p>In <span>{seconds}</span> Seconds</p> 
        <button on:click="{rl}">Retry</button>
    </div>
  </div>
  {/if}

  <div class="data-container">
    <p>Pairs: <span>{pairsCount}/10</span></p>
    <p>Flips: <span>{flipsCount}</span></p>
    <p>Seconds: <span>{seconds}</span></p>
  </div>

  <div class="memory-container">

      <div class="fruits-container">
        {#each arr as fruit}
        <div class="flip" id="{fruit.Class}">
          <div class="inner" id="{fruit.Class}">
            <div class="fruit">
              <img class="{fruit.Class2}" src="{fruit.Src}" alt="Fruit">
            </div>
              <div on:click="{(e) => selected.push(fruit.Name)}" on:click="{check}" class="back">
                <!-- <img src="https://media.istockphoto.com/photos/abstract-background-picture-id507279130?b=1&k=20&m=507279130&s=170667a&w=0&h=w5qwQoTuVPQT4bqMhtmHDhb6I7FuzA8D7emrj4gEoy4=" alt="Background"> -->
              </div>
          </div>
        </div>
        {/each}
    </div>

  </div>
</main>

<style>

  h1 {
    color: #251E30;
  }

  p {
    color: #251E30;
  }

  .data-container {
    display: flex;
    justify-content: center;
  }

  .data-container > p {
    display: flex;
    justify-content: center;
    margin-right: 25px;
    font-size: 19px;
  }

  .data-container > p > span {
    font-size: 20px;
    font-weight: 700;
  }

  .memory-container {
    display: flex;
    justify-content: center;
    background-color: #FEF6FF;
    padding: 17px 25px 25px 17px;
    border: 3px solid #251E30;
    border-radius: 15px;
  }

  .fruits-container {
    display: grid;
    justify-items: center;
    grid-template-columns: auto auto auto auto;
    grid-gap: 15px;
  }

  .fruit {
    display: flex;
    justify-content: center;
    border: 2px solid rgb(27, 3, 13);
    border-radius: 10px;
    transform: rotateY(180deg);
    position: absolute;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: 10px;
    cursor: pointer;
  }

  .fruit > img {
    width: 110px;
    height: 115px;
    border-radius: 10px;
    border: 2px solid rgb(0, 0, 0);
  }

  .flip {
    background-color: transparent;
    width: 110px;
    height: 115px;
    perspective: 1000px;
  }

  .inner {
    position: relative;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  .back {
    position: absolute;
    width: 115px;
    height: 122px;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: 10px;
    border: 2px solid #A27DE6;
  }

  .back {
    background-color: #251E30;
    grid-gap: 15px;
    cursor: pointer;
  }

  /* .back > img {
    width: 115px;
    height: 122px;
    border-radius: 10px;
  } */

  #turn {
    transform: rotateY(180deg);
  }

  .selected {
    opacity: 0.7;
    border: 2px solid rgba(255, 217, 0, 0.77) !important;
    /* box-shadow:
    inset 0 0 50px #fff,      
    inset 20px 0 80px #f0f,   
    inset -20px 0 80px #0ff, 
    inset 20px 0 300px #f0f, 
    inset -20px 0 300px #0ff, 
    0 0 50px #fff,            
    -10px 0 80px #f0f,       
    10px 0 80px #0ff;  */

  }

  .modal {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    opacity: 0;
    visibility: hidden;
    transform: scale(1.1);
    transition: visibility 0s linear 0.25s, opacity 0.25s 0s, transform 0.25s;
    z-index: 10;
  }

  .modal-content {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: #FF6F91;
      padding: 1rem 1.5rem;
      width: 24rem;
      border-radius: 0.5rem;
      border: 2px solid #845EC2;
  }

  .modal-content > h1 {
    color: #F9F871;
    text-shadow: -1px -1px 0 #845EC2, 1px -1px 0 #845EC2, -1px 1px 0 #845EC2, 1px 1px 0 #845EC2;
    padding: 0rem;
    margin: 0.5rem 0rem;
  }

  .modal-content > p {
      color: #F9F871;
      font-weight: 700;
      text-shadow: -1px -1px 0 #845EC2, 1px -1px 0 #845EC2, -1px 1px 0 #845EC2, 1px 1px 0 #845EC2;
  }

  .modal-content > p > span {
      color: #ffffff;
      font-weight: 700;
      text-shadow: -1px -1px 0 #000000, 1px -1px 0 #000000, -1px 1px 0 #000000, 1px 1px 0 #000000;
  }

  .modal-content > button {
      color: #F9F871;
  	  background: #D65DB1;
      width: 12rem;
      height: 3rem;
      font-size: 1.5rem;
      font-weight: 700;
      padding: 0rem;
      border: 2px solid #FF9671;
      text-shadow: -1px -1px 0 #845EC2, 1px -1px 0 #845EC2, -1px 1px 0 #845EC2, 1px 1px 0 #845EC2;
  }

  .modal-content > button:hover {
    background: #53d8d1;
    transition: background 0.5s ease-in-out;
  }

  .show-modal {
      opacity: 1;
      visibility: visible;
      transform: scale(1.0);
      transition: visibility 0s linear 0s, opacity 0.25s 0s, transform 0.25s;
  }

    @keyframes confetti-spin {
    0% {
      transform: rotate3d(0, 1, 1, 360deg);
    }

    50% {
      transform: rotate3d(0, 1, 1, 180deg);
    }
    
    100% {
      transform: rotate3d(0, 0, 0, 0);
    }
  }

  @keyframes confetti-fall {
    0% {
      transform: translateY(0px);
      opacity: 1;
    }

    50% {
      opacity: 1;
    }

    100% {
      transform: translateY(110vh);
      opacity: 0;
    }
  }

  .confetti {
    position: fixed;
    animation: confetti-fall 2s ease-out infinite;
    width: 20px;
    height: 20px;
  }

  .confetti::before {
    content: "";
    display: block;
    width: 100%;
    height: 100%;
    animation: confetti-spin 1s linear infinite;
  }

  .confetti:nth-child(1)::before {
    background-color: #E84FA9;
  }

  .confetti:nth-child(2)::before {
    background-color: #6A737D;
    animation-delay: -4s;
    animation-fill-mode: backwards;
    animation-duration: 1.5s;
  }

  .confetti:nth-child(3)::before {
    background-color: #1369D3;
    animation-delay: -3s;
  }

  .confetti:nth-child(4)::before {
    background-color: #30A64B;
    animation-delay: -2.5s;
    animation-fill-mode: backwards;
    animation-duration: 1.2s;
  }

  .confetti:nth-child(5)::before {
    background-color: #6F47BF;
    animation-delay: -4s;
  }

  .confetti:nth-child(6)::before {
    background-color: #F46A23;
    animation-delay: -6s;
    animation-fill-mode: backwards;
    animation-duration: 1.1s;
  }

  .confetti:nth-child(7)::before {
    background-color: #FED24E;
    animation-delay: -1.5s;
  }

  .confetti:nth-child(8)::before {
    background-color: #1369D3;
    animation-delay: -2s;
    animation-fill-mode: backwards;
    animation-duration: 1.8s;
  }

  .confetti:nth-child(9)::before {
    background-color: #E84FA9;
    animation-delay: -3.5s;
  }

  .confetti:nth-child(10)::before {
    background-color: #6F47BF;
    animation-delay: -2.5s;
    animation-fill-mode: backwards;
    animation-duration: 1.3s;
  }

  .confetti:nth-child(11)::before {
    background-color: #E84FA9;
  }

  .confetti:nth-child(12)::before {
    background-color: #6A737D;
    animation-delay: -5s;
    animation-fill-mode: backwards;
    animation-duration: 1.5s;
  }

  .confetti:nth-child(13)::before {
    background-color: #1369D3;
    animation-delay: -3s;
  }

  .confetti:nth-child(14)::before {
    background-color: #30A64B;
    animation-delay: -2.5s;
    animation-fill-mode: backwards;
    animation-duration: 1.2s;
  }

  .confetti:nth-child(15)::before {
    background-color: #6F47BF;
    animation-delay: -4s;
  }

  .confetti:nth-child(16)::before {
    background-color: #F46A23;
    animation-delay: -6s;
    animation-fill-mode: backwards;
    animation-duration: 1.1s;
  }

  .confetti:nth-child(17)::before {
    background-color: #FED24E;
    animation-delay: -1.5s;
  }

  .confetti:nth-child(18)::before {
    background-color: #1369D3;
    animation-delay: -2s;
    animation-fill-mode: backwards;
    animation-duration: 1.8s;
  }

  .confetti:nth-child(19)::before {
    background-color: #E84FA9;
    animation-delay: -3.5s;
  }

  .confetti:nth-child(20)::before {
    background-color: #6F47BF;
    animation-delay: -2.5s;
    animation-fill-mode: backwards;
    animation-duration: 1.3s;
  }

  .confetti:nth-child(1) {
    left: 10%;
    width: 20px;
    height: 20px;
  }

  .confetti:nth-child(2) {
    left: 20%;
    animation-delay: -4s;
    width: 15px;
    height: 15px;
  }

  .confetti:nth-child(3) {
    left: 30%;
    animation-delay: -3.2s;
    width: 10px;
    height: 10px;
  }

  .confetti:nth-child(4) {
    left: 40%;
    animation-delay: -2.5s;
    width: 12px;
    height: 12px;
  }

  .confetti:nth-child(5) {
    left: 50%;
    animation-delay: -4.1s;
    transform: scale(1.3);
  }

  .confetti:nth-child(6) {
    left: 60%;
    animation-delay: -6.8s;
    width: 16px;
    height: 16px;
  }

  .confetti:nth-child(7) {
    left: 70%;
    animation-delay: -1.5s;
    width: 18px;
    height: 18px;
  }

  .confetti:nth-child(8) {
    left: 80%;
    animation-delay: -2s;
    width: 22px;
    height: 22px;
  }

  .confetti:nth-child(9) {
    left: 90%;
    animation-delay: -3.5s;
    width: 8px;
    height: 8px;
  }

  .confetti:nth-child(10) {
    left: 100%;
    animation-delay: -2.5s;
    width: 24px;
    height: 24px;
  }

  .confetti:nth-child(11) {
    left: 10%;
    width: 20px;
    height: 20px;
  }

  .confetti:nth-child(12) {
    left: 20%;
    animation-delay: -4s;
    width: 15px;
    height: 15px;
  }

  .confetti:nth-child(13) {
    left: 30%;
    animation-delay: -3.2s;
    width: 10px;
    height: 10px;
  }

  .confetti:nth-child(14) {
    left: 40%;
    animation-delay: -2.5s;
    width: 12px;
    height: 12px;
  }

  .confetti:nth-child(15) {
    left: 50%;
    animation-delay: -4.1s;
    transform: scale(1.3);
  }

  .confetti:nth-child(16) {
    left: 60%;
    animation-delay: -6.8s;
    width: 16px;
    height: 16px;
  }

  .confetti:nth-child(17) {
    left: 70%;
    animation-delay: -1.5s;
    width: 18px;
    height: 18px;
  }

  .confetti:nth-child(18) {
    left: 80%;
    animation-delay: -2s;
    width: 22px;
    height: 22px;
  }

  .confetti:nth-child(19) {
    left: 90%;
    animation-delay: -3.5s;
    width: 8px;
    height: 8px;
  }

  .confetti:nth-child(20) {
    left: 100%;
    animation-delay: -2.5s;
    width: 24px;
    height: 24px;
  }


</style>
