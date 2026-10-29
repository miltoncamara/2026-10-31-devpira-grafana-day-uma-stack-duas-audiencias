<script setup lang="ts">
// Decoração minimalista com cara de dashboard: séries temporais, linha de
// limiar de alerta e pequenos painéis. Desenho original, sem logos.
const props = withDefaults(defineProps<{
  seriesY?: number   // deslocamento vertical das séries (base do slide = 0)
  panelsX?: number
  panelsY?: number
}>(), { seriesY: 0, panelsX: 708, panelsY: 48 })
</script>

<template>
  <svg
    class="absolute inset-0 w-full h-full pointer-events-none"
    viewBox="0 0 980 552"
    preserveAspectRatio="none"
    aria-hidden="true"
  >
    <defs>
      <linearGradient id="obs-fade-orange" x1="0" x2="1" y1="0" y2="0">
        <stop offset="0" stop-color="#F2994A" stop-opacity="0" />
        <stop offset="0.45" stop-color="#F2994A" stop-opacity="0.35" />
        <stop offset="1" stop-color="#F2994A" stop-opacity="0.9" />
      </linearGradient>
      <linearGradient id="obs-fade-blue" x1="0" x2="1" y1="0" y2="0">
        <stop offset="0" stop-color="#6FB1E6" stop-opacity="0" />
        <stop offset="1" stop-color="#6FB1E6" stop-opacity="0.4" />
      </linearGradient>
    </defs>

    <!-- Séries temporais -->
    <g :transform="`translate(0 ${props.seriesY})`" fill="none" stroke-linecap="round">
      <path
        d="M0,525 C80,520 120,505 180,512 S300,530 360,515 S480,495 540,505 S680,525 740,508 S880,490 980,500"
        stroke="url(#obs-fade-blue)" stroke-width="1.5"
      />
      <path
        d="M0,500 C60,490 90,470 140,480 S220,510 270,490 S350,440 400,455 S480,500 530,470 S610,400 660,420 S740,470 790,440 S870,380 980,395"
        stroke="url(#obs-fade-orange)" stroke-width="2"
      />
      <!-- Limiar de alerta e o ponto que o cruzou -->
      <line x1="620" y1="410" x2="980" y2="410" stroke="#F2994A" stroke-opacity="0.35" stroke-width="1" stroke-dasharray="4 6" />
      <circle cx="884" cy="384" r="9" stroke="#F2994A" stroke-opacity="0.35" stroke-width="1" />
      <circle cx="884" cy="384" r="3.5" fill="#F2994A" />
    </g>

    <!-- Painéis de dashboard -->
    <g :transform="`translate(${props.panelsX} ${props.panelsY})`">
      <g fill="#161D26" stroke="#2A3240" stroke-width="1">
        <rect x="0" y="0" width="72" height="48" rx="6" />
        <rect x="84" y="0" width="72" height="48" rx="6" />
        <rect x="168" y="0" width="72" height="48" rx="6" />
        <rect x="0" y="60" width="156" height="48" rx="6" />
        <rect x="168" y="60" width="72" height="48" rx="6" />
      </g>
      <!-- barras -->
      <g fill="#F2994A">
        <rect x="16" y="28" width="8" height="10" rx="1.5" fill-opacity="0.5" />
        <rect x="32" y="20" width="8" height="18" rx="1.5" fill-opacity="0.7" />
        <rect x="48" y="14" width="8" height="24" rx="1.5" />
      </g>
      <!-- medidor -->
      <path d="M100,36 A20,20 0 0 1 140,36" fill="none" stroke="#2A3240" stroke-width="4" stroke-linecap="round" />
      <path d="M100,36 A20,20 0 0 1 132,20" fill="none" stroke="#6FB1E6" stroke-width="4" stroke-linecap="round" />
      <!-- valor único -->
      <rect x="184" y="16" width="40" height="7" rx="3.5" fill="#F3F1EB" fill-opacity="0.85" />
      <rect x="184" y="29" width="24" height="4" rx="2" fill="#AEB8C4" fill-opacity="0.5" />
      <!-- sparkline -->
      <polyline
        points="14,94 34,88 54,92 74,78 94,84 114,72 142,76"
        fill="none" stroke="#F2994A" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"
      />
      <!-- status ok -->
      <circle cx="204" cy="84" r="6" fill="#3FB57F" fill-opacity="0.85" />
    </g>
  </svg>
</template>
