<template>
    <div class="titlebar" >
        <img v-bind:src="ico">
        <div class="bar" @dbclick="atualizaMax(isMax)">
            <slot></slot>
            <div class="dragregion" >
                <span>{{title}}</span>
            </div>

            <div class="button" @click="onMinimize"><span class="dash">&#x2012;</span></div>
            <div class="button" @click="onMaximize"><span>&#9744;</span></div>
            <div class="button close" @click="onClose"><span>&#10005;</span></div>
        </div>
    </div>
</template>

<script>


const remote = require('electron').remote;

let win = remote.getCurrentWindow()

export default {
    name: 'TitleBar',
    props: [ 'title', 'ico' ],
    methods: {
        onClose() {
            close()
        },
        onMinimize() {
            win.minimize()
        },
        onMaximize() {
            if(win.isMaximized()) 
               win.unmaximize()
            else
               win.maximize()
            
        },
        atualizaMax(isMax) {
            console.log(isMax)
            return isMax ? this.isMax = false : this.isMax = true
        } 

    }
}
</script>

<style scoped>
:root {
    --bg-color: #fff;
    --btn-hover-color: rgb(0, 0, 0, 0.1);
}


.square {
    height: 9px;
    max-width: 9px;
    border: 1px solid black;
    background-color: var(--bg-color);
}

.titlebar {
    display: flex;
    color: var(--vue-electron-titlebar-color);
    background-color: var(--bg-color);
    height: 30px;
    margin: 0;
    padding: 0;
}
img {
    height: 25px;
}
.bar {
    flex-grow: 1; 
    display: flex;
}
.dragregion {
    flex-grow: 1;
    text-align: center;
    vertical-align: middle;
    margin: 3px 3px 0px 0px;
    -webkit-app-region: drag;
    display: flex;
    align-items: center;        
}
.dragregion>span {
    flex-grow: 1;   
    margin-top: -3px;        
}
.button {
    width: 44px;
    text-align: center;
    font-size: 12pt;
    display: flex;
    align-items: center;        
}
.button>span {
    flex-grow: 1;   
    margin-top: -3px;
    user-select: none;
}
.button:hover {
    background: rgba(8, 8, 8, 0.1);
}

.button:active {
  background: rgba(10, 10, 10, 0.2);
}

.close:hover {
    background: #E81123 !important;
    color: white;
}
.close:active {
  background: #F1707A !important;
}

.button>span.dash {
    vertical-align: sub;
    margin-top: 0px;
}
</style>