<g transform={`translate(${translation}, 0)`}>
    {#each days as day}
        <Cell
            color={day.color}
            date={day.date}
            radius={cellRadius}
            size={cellSize}
            value={day.value}
            x={getCustomDay(day.date.getDay()) * cellRect}
            y={(getWeekIndex(day.date) * cellRect) + monthLabelHeight}
            mouseLeave={day.mouseLeave}
            mouseDown={day.mouseDown}
            mouseEnter={day.mouseEnter}
            data={day.data}
        />
    {/each}
    {#if monthLabelHeight > 0}
        <text
            alignment-baseline="hanging"
            fill={fontColor}
            font-family={fontFamily}
            font-size={fontSize}
            x="0"
            y="0">
            {monthLabels[days[0].date.getMonth()]}
        </text>
    {/if}
</g>

<script>
import Cell from './Cell.svelte';
import { getWeekIndex } from '../utils/date';

$: translation = (((7 * cellRect) - cellGap) + monthGap) * index;

export let cellGap;
export let cellRadius;
export let cellRect;
export let cellSize;
export let days;
export let fontColor;
export let fontFamily;
export let fontSize;
export let index;
export let monthGap;
export let monthLabelHeight;
export let monthLabels;

function getCustomDay(day) {
    day -= 1;

    if(day === -1) {
        day = 6;
    }

    return day;
}
</script>