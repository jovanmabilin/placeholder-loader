<template>
    <div>
        <div class="placeholder-content">
            <b-row>
                <b-col v-for="indexColumn in column" :key="indexColumn">
                    <div  class="placeholder-content-item-container" v-for="indexRow in row" :key="indexRow">
                        <div v-if="indexColumn === 1" class="placeholder-content-item" style="width: 12px; height: 12px;"></div>
                        <div class="placeholder-content-item" :style="placeholderItemStyle()"></div>
                    </div>
                </b-col>
            </b-row>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            row: {
                type: Number,
                default: 10,
            },
            column: {
                type: Number,
                default: 1
            }
        },
        data() {
            return { 
                isLoading: true,
                randomWidth: [20,30,40,50,60],
            }
        },
        methods: {
            placeholderItemStyle() {
                let random = Math.ceil( Math.random() * ( this.randomWidth.length - 1) );
                let randomWidth = this.randomWidth[random];
                return {
                    width: `${randomWidth}%`,
                    height: '12px',
                }
            }
        },
    }
</script>

<style lang="scss" scoped>
.placeholder-content {
  width: 100%;
  height: inherit;
  animation: reduce-opacity 2s linear infinite;
}

.placeholder-content .placeholder-content-item  {
  border-radius: 50px;
  margin-bottom: 10px;
  background-color: #dddddd80;
}

.placeholder-content-item-container .placeholder-content-item  {
    display: inline-block;
}

@keyframes reduce-opacity {
      0% { -webkit-filter:    opacity(1);}
      50% { -webkit-filter:   opacity(.1);}
      100% { -webkit-filter:  opacity(1);}
}
</style>