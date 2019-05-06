<template>
    <button class="g-button" :class="{[`icon-${iconPosition}`]: true}" >
        <g-icon class="icon" :name="icon"></g-icon>
        <div class="content">
            <slot></slot>
        </div>

    </button>
</template>
<script>
   // import Icon from "./icon";
    export default {
        //components: {Icon},
        // props:['icon','iconPosition']
        props: {
            icon: {},
            iconPosition: {
                type: String,
                default: 'left',
                //属性检查器
                validate: function (value) {
                    return !(value !== 'left' && value !== 'right')
                }
            }
        }
    }
</script>
<style lang="scss">
    .g-button{
        font-size: var(--font-size);height: var(--button-height);
        border-radius: var(--border-radius);background: var(--button-bg);border:1px solid var(--border-color);
        display: inline-flex;justify-content: center;align-items: center;
        vertical-align: middle;padding: 0 1em;

        &:hover{border-color:var(--border-color-hover);}
        &:active{background-color:var(--button-active-bg);}
        &:focus{outline: none;}
        > .icon{order:1; margin-right: .1em}
        > .content{order:2}
        &.icon-right{
            > .icon{order:2; margin-left: .1em; margin-right: 0;}
            > .content{order:1;}
        }
    }

</style>