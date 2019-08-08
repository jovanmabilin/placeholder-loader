<template>
    <div>
        <table class="table b-table table-hover table-sm border ">
            <thead>
                <tr v-if="field.length" class="placeholder-content">
                    <th v-for="(item,index) in field" :key="index" :aria-colindex="index" :class="['placeholder-content-item-container',item.thClass]" :style="item.thStyle || null">
                        <div v-if="index === 0" class="placeholder-content-item" style="width: 12px; height: 12px;"></div>
                         <div class="placeholder-content-item" :style="placeholderItemStyle()"></div>
                    </th>
                </tr>
            </thead>
            <tbody class="placeholder-content">
                <tr v-for="indexRow in row - 1" :key="indexRow">
                    <td v-for="(item,index) in field" :key="index" :class="['placeholder-content-item-container',item.tdClass]">
                        <div v-if="index === 0" class="placeholder-content-item" style="width: 12px; height: 12px;"></div>
                        <div class="placeholder-content-item" :style="placeholderItemStyle()"></div>
                    </td>
                </tr>
            </tbody>
        </table>
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
            },
            field: {
                type: Array,
                default: [],
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