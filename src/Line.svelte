<script>
    export let style = 'full';
    export let label = '';
    export let headArrow = false;
    export let x1;
    export let y1;
    export let x2;
    export let y2;
</script>

<style>
svg {
    stroke: black;
}

text {
    dominant-baseline: ideographic;
    font-size: 20px;
}

.dashed {
    stroke-dasharray: 10 5;
}
</style>

<svg>
    <defs>
        <marker
            id="triangle"
            markerWidth="10"
            markerHeight="10"
            orient="auto-start-reverse"
            refX="10"
            refY="5"
            viewBox="0 0 10 10"
        >
            <polygon points="0,0 10,5 0,10" />
        </marker>
    </defs>
    <line
        id={label}
        class:dashed={style === "dashed"}
        {x1}
        {y1}
        {x2}
        {y2}
        marker-start={headArrow ? "url(#triangle)" : undefined}
    />
    <text>
        <textPath href="#{label}" startOffset="50%" text-anchor="middle">{label}</textPath>
    </text>
</svg>
