<rect
    data-date={stringifyDate(date)}
    data-value={value}
    fill={color}
    height={size}
    rx={radius}
    width={size}
    x={x}
    y={y}
    on:mouseout={mouseOut}
    on:mouseover={mouseOver}
/>

<script>
import { stringifyDate } from '../utils/date';

export let color;
export let date;
export let radius;
export let size;
export let value;
export let x;
export let y;
export let data;
export let mouseEnter;
export let mouseLeave;

const getEventData = (event) => {
    return {
        ...data,
        pos: event.target.getBoundingClientRect
    }
}

const mouseOut = (event) => {
    mouseLeave(getEventData(event));
}
const mouseOver = (event) => {
    mouseEnter(getEventData(event));
}
</script>
