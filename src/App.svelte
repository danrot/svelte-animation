<script>
    import {tweened} from 'svelte/motion';
    import Node from './Node.svelte';
    import Line from './Line.svelte';

    const mainLineX = 300;
    const leftLineX = mainLineX - 200;
    const rightLineX = mainLineX + 200;

    const eventX = 700;
    const eventY = 300;

    const htmlX = mainLineX;
    const htmlY = 100;

    const bodyX = mainLineX;
    const bodyY = 300;

    const formX = mainLineX;
    const formY = 500;

    const inputX = leftLineX;
    const inputY = 700;

    const buttonX = rightLineX;
    const buttonY = 700;

    const targetPositions = [
        {x: buttonX, y: buttonY - 50},
        {x: formX + 100, y: formY},
        {x: bodyX + 100, y: bodyY},
        {x: htmlX + 100, y: htmlY},
    ];

    const currentTargetX = tweened(targetPositions[0].x);
    const currentTargetY = tweened(targetPositions[0].y);

    let targetPositionIndex = 0;

    $: targetPositionsLength = targetPositions.length;

    $: {
        currentTargetX.set(targetPositions[targetPositionIndex].x);
        currentTargetY.set(targetPositions[targetPositionIndex].y);
    }
</script>

<svg width="800" height="800">
    <Line x1={htmlX} y1={htmlY} x2={bodyX} y2={bodyY} />
    <Node x={htmlX} y={htmlY}>html</Node>
    <Line x1={bodyX} y1={bodyY} x2={formX} y2={formY} />
    <Node x={bodyX} y={bodyY}>body</Node>
    <Line x1={formX} y1={formY} x2={inputX} y2={inputY} />
    <Line x1={formX} y1={formY} x2={buttonX} y2={buttonY} />
    <Node x={formX} y={formY}>form</Node>
    <Node x={inputX} y={inputY}>input</Node>
    <Node x={buttonX} y={buttonY}>button</Node>

    <Node style="rect" x={eventX} y={eventY}>event</Node>
    <Line label="target" headArrow={true} style="dashed" x1={buttonX} y1={buttonY - 50} x2={eventX} y2={eventY + 50} />
    <Line label="currentTarget" headArrow={true} style="dashed" x1={$currentTargetX} y1={$currentTargetY} x2={eventX - 100} y2={eventY} />
</svg>

<div>
    <button disabled={targetPositionIndex <= 0} on:click={() => targetPositionIndex -= 1}>Previous</button>
    <button disabled={targetPositionIndex >= targetPositionsLength - 1} on:click={() => targetPositionIndex += 1}>Next</button>
</div>
