<template>
<div>
    <div class="topnav">
    <a class="active" href="#home">Elevator functions</a>
    </div> 
   <div class="wrapper">
    <div class="main" id="app">
        <div class="main-levator">
            <div class="shaft"><div class="elevator elevator1 " :class="classposition1">1</div></div>
            <div class="shaft"><div class="elevator elevator2 " :class="classposition2">2</div></div>
            <div class="shaft"><div class="elevator elevator3 " :class="classposition3">3</div></div>
        </div>
        <div class="main-floors">
            <div class="floor floor6"><button class="btn2" @click="move(20)">20</button></div>
            <div class="floor floor5"><button class="btn3" @click="move(19)">19</button></div>
            <div class="floor floor4"><button class="btn4" @click="move(18)">18</button></div>
            <div class="floor floor3"><button class="btn5" @click="move(17)">17</button></div>
            <div class="floor floor2"><button class="btn6" @click="move(16)">16</button></div>
            <div class="floor floor1"><button class="btn7" @click="move(15)">15</button></div>
            <div class="floor floor7"><button class="btn1" @click="move(14)">14</button></div>
            <div class="floor floor6"><button class="btn2" @click="move(13)">13</button></div>
            <div class="floor floor5"><button class="btn3" @click="move(12)">12</button></div>
            <div class="floor floor4"><button class="btn4" @click="move(11)">11</button></div>
            <div class="floor floor3"><button class="btn5" @click="move(10)">10</button></div>
            <div class="floor floor2"><button class="btn6" @click="move(9)">9</button></div>
            <div class="floor floor1"><button class="btn7" @click="move(8)">8</button></div>
            <div class="floor floor7"><button class="btn1" @click="move(7)">7</button></div>
            <div class="floor floor6"><button class="btn2" @click="move(6)">6</button></div>
            <div class="floor floor5"><button class="btn3" @click="move(5)">5</button></div>
            <div class="floor floor4"><button class="btn4" @click="move(4)">4</button></div>
            <div class="floor floor3"><button class="btn5" @click="move(3)">3</button></div>
            <div class="floor floor2"><button class="btn6" @click="move(2)">2</button></div>
            <div class="floor floor1"><button class="btn7" @click="move(1)">1</button></div>
        </div>

    </div>
</div>
</div>
</template>

<script>
export default {
    data(){
        return{
            elevator:{
                count: 0,
                elevatorsOnePosition: 0,
                elevatorsTwoPosition: 0,
                elevatorsThreePosition: 0,
            },
            classposition1: 'position1',
            classposition2: 'position1',
            classposition3: 'position1'
        }
    },
    methods:{
        move(no){
            // console.log(no,e)
            const result1 = no - this.elevator.elevatorsOnePosition
            const result2 = no - this.elevator.elevatorsTwoPosition
            const result3 = no - this.elevator.elevatorsThreePosition
            let res1 = Math.abs(result1)
            let res2 = Math.abs(result2)
            let res3 = Math.abs(result3)
           this.evaluate(no,res1,res2,res3)
        },
        evaluate(no,res1,res2,res3){
            console.log(res1,res2,res3)
               var claspos = 'position'+ no
            if(no == 6){
                this.elevator.elevatorsTwoPosition = no
                console.log(claspos)
                this.classposition2 = claspos
                return
            }
            if(no == 3){
                if(res1<res3){
                this.elevator.elevatorsOnePosition = no
                console.log(claspos)
                this.classposition1 = claspos
                return

                }else{
                this.elevator.elevatorsThreePosition = no
                console.log(claspos)
                this.classposition3 = claspos
                return

                }
            }
            if(res2 < res3){
                this.elevator.elevatorsThreePosition = no
                console.log(claspos)
                this.classposition2 = claspos
                return
            }
            if((res1 == res2) && ( res1 == res3)){
                this.elevator.elevatorsThreePosition = no
                console.log(claspos)
                this.classposition3 = claspos
                return
            }
            if((res1 < res2) && (res1 < res3)){
                 this.elevator.elevatorsOnePosition = no
                console.log(claspos)
                this.classposition1 = claspos
                return
            }
            if((res2 < res1) && (res2 < res3)){
                 this.elevator.elevatorsTwoPosition = no
                console.log(claspos)
                this.classposition2 = claspos
                return
            }
            if((res3 < res1) && (res3 < res2)){
                 this.elevator.elevatorsThreePosition = no
                console.log(claspos)
                this.classposition3 = claspos
                return
            }
            if((res2 = res3)){
                 this.elevator.elevatorsTwoPosition = no
                console.log(claspos)
                this.classposition2 = claspos
                return
            }
            if((res2 = res1)){
                 this.elevator.elevatorsThreePosition = no
                console.log(claspos)
                this.classposition3 = claspos
                return
            }

        }
    }

}
</script>

<style>
*{
    margin: 0;
    padding: 0;
}
.wrapper {
    display: flex;
    justify-items: center;
    align-items: center;
    justify-content: center;
    width: 900px;
    margin: 20px;
}
.main{
    display: flex;
    justify-content:end;
    align-items: end;
    justify-items: end;
}
.main-levator{
    background-color: aquamarine;
    height: 900px;
    display: flex;
    justify-items: center;
    align-items: center;
}
.main-floors{
    background-color: beige;
    height: 900px;
    width: 100px;
}
.elevator{
    width: 50px;
    height: 40px;
    /* border-right: black 2px solid; */
}
.floor{
    padding: 10px;
    border-top: black 2px solid;
}
.shaft{
    position: relative;
    height: 900px;
    width: 50px;
    border: black 2px solid;

}
.elevator1{
    position: absolute;
    padding: auto;
    right: 0px;
    background-color: brown;
}
.elevator2{
    position: absolute;
    padding: auto;
    right: 0px;
    background-color: green;
}
.elevator3{
    position: absolute;
    padding: auto;
    right: 0px;
    background-color: blue;
}
.position1{
    bottom: 0px;
}
.position2{
    bottom: 35px;
}
.position3{
    bottom: 80px;
}
.position4{
    bottom: 125px;
}
.position5{
    bottom: 170px;
}
.position6{
    bottom: 240px;
}
.position7{
    bottom: 260px;
}
.position8{
    bottom: 310px;
}
.position9{
    bottom: 370px;
}
.position10{
    bottom: 420px;
}
.position11{
    bottom: 460px;
}
.position12{
    bottom: 500px;
}
.position13{
    bottom: 550px;
}
.position14{
    bottom: 590px;
}
.position15{
    bottom: 640px;
}
.position16{
    bottom: 680px;
}
.position17{
    bottom: 720px;
}
.position18{
    bottom: 770px;
}
.position19{
    bottom: 810px;
}
.position20{
    bottom: 855px;
}




/* Add a black background color to the top navigation */
.topnav {
  background-color: #333;
  overflow: hidden;
}

/* Style the links inside the navigation bar */
.topnav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

/* Change the color of links on hover */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}

/* Add a color to the active/current link */
.topnav a.active {
  background-color: #04AA6D;
  color: white;
}
</style>