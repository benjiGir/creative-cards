<template>
    <div @mouseover="showOptions = true"
         @mouseleave="showOptions = false">
        <transition name="fade">
            <form class="small" v-show="showOptions">
            <label for="selectBox">Font size: </label>
                <select class="custom-select" id="selectBox" v-model="setFontSize">
                    <option value="42">42px</option>
                    <option value="48">48px</option>
                    <option value="56">56px</option>
                    <option value="64">64px</option>
                </select>
                <div class="form-check form-check-inline">
                    <label class="form-check-label" for="textLeft">
                        <input type="radio" value="Left" id="textLeft" class="form-check-input" v-model="setTextAlign"> Left
                    </label>
                </div>
                <div class="form-check form-check-inline">
                    <label class="form-check-label" for="textCenter">
                        <input type="radio" value="center" id="textCenter" class="form-check-input" v-model="setTextAlign"> Center
                    </label>
                </div>
                <div class="form-check form-check-inline">
                    <label class="form-check-label" for="textRight">
                        <input type="radio" value="right" id="textRight" class="form-check-input" v-model="setTextAlign"> Right
                    </label> 
                </div>
                <div class="form-check form-check-inline">
                    <label class="form-check-label">
                        <input class="form-check-input" type="checkbox" id="textBold" v-model="setBold"> Bold
                    </label>
                </div>
                <div class="form-check form-check-inline">
                    <label class="form-check-label">
                        <input class="form-check-input" type="checkbox" id="textItalic" v-model="setItalic"> Italic
                    </label>
                </div>
            </form>
        </transition>
        
        <p :style="styleObject" 
           :class="{ bold: setBold, italic: setItalic}">
            {{ displayText }}
        </p>
    </div>
</template>

<script>
export default {
    props: {
        displayText: [String],
        containerHeight: {
            type: Number,
            default: 200
        }
    },
    data: function() {
        return {
            showOptions: false,
            setFontSize: '',
            setTextAlign: '',
            setBold: false,
            setItalic: false
        }
    },
    computed: {
        styleObject: function() {
            return {
                height: this.containerHeight + 'px',
                fontSize: this.setFontSize + 'px',
                textAlign: this.setTextAlign
            }
        }
    }
}
</script>

<style scoped>
    p {
        font-family: 'Press Start 2P', cursive;
        font-size: 42px;
        line-height: 42px;
        text-shadow: 2px 2px 2px #aaa;
        color: #4d4d4d;
        margin: 5px 0;
        border: 1px dotted grey;
        white-space: pre-line;
        overflow: hidden;
    }
    .custom-select {
        width: 20%;
    }

    .form-check-inline {
        margin-right: 0.35rem;
    }
    .bold {
        font-weight: bold;
    }
    .italic {
        font-style: italic;
    }

    form {
        position: absolute;
        border-bottom: 1px dotted grey;
        margin-top: 10px;
        margin-bottom: 5px;
        padding-bottom: 5px;
    }
    select {
        height: 40%;
    }

    
    
</style>