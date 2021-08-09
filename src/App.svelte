<script>
    import Node from './Node.svelte';
    import Line from './Line.svelte';

    const mainLineX = 300;
    const leftLineX = mainLineX - 200;
    const rightLineX = mainLineX + 200;

    const eventX = 700;
    const eventY = 300;
</script>

<svg width="800" height="1000">
    <Node x={mainLineX} y="100">html</Node>
    <Line x1={mainLineX} y1="150" x2={mainLineX} y2="250" />
    <Node x={mainLineX} y="300">body</Node>
    <Line x1={mainLineX} y1="350" x2={mainLineX} y2="450" />
    <Node x={mainLineX} y="500">form</Node>
    <Line x1={mainLineX} y1="550" x2={leftLineX} y2="650" />
    <Line x1={mainLineX} y1="550" x2={rightLineX} y2="650" />
    <Node x={leftLineX} y="700">input</Node>
    <Node x={rightLineX} y="700">button</Node>

    <Node style="rect" x={eventX} y={eventY}>event</Node>
    <Line label="target" style="dashed" x1={rightLineX} y1="650" x2={eventX} y2={eventY + 50} />
    <Line label="currentTarget" style="dashed" x1={rightLineX} y1="650" x2={eventX - 100} y2={eventY} />
</svg>
