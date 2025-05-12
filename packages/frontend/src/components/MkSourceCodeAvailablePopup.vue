<!--
SPDX-FileCopyrightText: syuilo and misskey-project
SPDX-License-Identifier: AGPL-3.0-only
-->

<template>
<div style="display: none;"></div>
</template>

<script lang="ts" setup>
import MkButton from '@/components/MkButton.vue';
import { host } from '@@/js/config.js';
import { i18n } from '@/i18n.js';
import { instance } from '@/instance.js';
import { miLocalStorage } from '@/local-storage.js';
import * as os from '@/os.js';

const emit = defineEmits<{
	(ev: 'closed'): void;
}>();

const zIndex = os.claimZIndex('low');

function close() {
	miLocalStorage.setItem('modifiedVersionMustProminentlyOfferInAgplV3Section13Read', 'true');
	emit('closed');
}
</script>

<style lang="scss" module>
.root {
	position: fixed;
	z-index: v-bind(zIndex);
	bottom: var(--MI-margin);
	left: 0;
	right: 0;
	margin: auto;
	box-sizing: border-box;
	width: calc(100% - (var(--MI-margin) * 2));
	max-width: 500px;
	display: flex;
}

.icon {
	text-align: center;
	padding-top: 25px;
	width: 100px;
	color: var(--MI_THEME-accent);
}
@media (max-width: 500px) {
	.icon {
		width: 80px;
	}
}
@media (max-width: 450px) {
	.icon {
		width: 70px;
	}
}

.main {
	padding: 25px 25px 25px 0;
	flex: 1;
}

.close {
	position: absolute;
	top: 8px;
	right: 8px;
	padding: 8px;
}

.title {
	font-weight: bold;
}

.text {
	margin: 0.7em 0 1em 0;
}
</style>
