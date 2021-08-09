<script>
    export let style = 'round';
    export let x = 0;
    export let y = 0;
    export let width = 200;
    export let height = 100;
</script>

<style>
rect {
    stroke: black;
    fill: white;
}

text {
    font-family: sans-serif;
    font-size: 30px;
    transform: translate(100px, 50px);
    text-anchor: middle;
    dominant-baseline: middle;
}

.round {
    rx: 100px;
}
</style>

<svg>
    <g transform="translate({x - width / 2} {y - height / 2})">
        <rect class:round={style === 'round'} {width} {height}></rect>
        <text>
            <slot />
        </text>
    </g>
</svg>
