<script>
    export let style = 'full';
    export let label = '';
    export let x1;
    export let y1;
    export let x2;
    export let y2;
</script>

<style>
svg {
    stroke: black;
}

.dashed {
    stroke-dasharray: 10 5;
}
</style>

<svg>
    <line id={label} class:dashed={style === "dashed"} {x1} {y1} {x2} {y2} />
    <text>
        <textPath href="#{label}" startOffset="50%" text-anchor="middle">{label}</textPath>
    </text>
</svg>
