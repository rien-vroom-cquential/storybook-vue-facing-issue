<template>
  <button type="button" :class="classes" @click="onClick" :style="style">{{ label }} </button>
</template>

<script lang="ts">

import {Component, Prop, Vue} from 'vue-facing-decorator';
import './button.css';
import { computed } from 'vue';

@Component()
    export default class Button extends Vue {
        @Prop() label!: string;
        @Prop({type: Boolean}) primary?: boolean;
        @Prop() size?: 'small' | 'medium' | 'large';
        @Prop() backgroundColor?: string;

        public get classes() {
            return {
              'storybook-button': true,
              'storybook-button--primary': this.primary,
              'storybook-button--secondary': !this.primary,
              [`storybook-button--${this.size || 'medium'}`]: true,
            }
        }

        public get style() {
            return {
              backgroundColor: this.backgroundColor
            }
        }

        public onClick() {
            this.emit('click', 1);
        }
    }
</script>
