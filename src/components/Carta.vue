<script setup>
const props = defineProps({
	carta: {
		type: Object,
		default: null,
	},
	horizontal: {
		type: Boolean,
		default: false,
	},
})

const retornaImagem = (carta) => {
	let naipe = ''
	if (!carta) {
		return `./cards/FUNDO.svg`
	}
	if (carta.naipe.nome === 'OUROS') {
		naipe = 'DIAMOND'
	}
	if (carta.naipe.nome === 'ESPADAS') {
		naipe = 'SPADE'
	}
	if (carta.naipe.nome === 'COPAS') {
		naipe = 'HEART'
	}
	if (carta.naipe.nome === 'PAUS') {
		naipe = 'CLUB'
	}
	let valor = ''
	if (carta) {
		valor = carta.valor
		return `./cards/${naipe}-${valor}.svg`
	}
	return ''
}

</script>

<template>
	<img :class="horizontal ? 'rotate-90 -my-[0.5vw]' : 'mx-[0.5vw]'" class="w-[5vw]" :src="retornaImagem(carta)" />
</template>
