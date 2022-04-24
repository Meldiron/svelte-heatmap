<path
    data-date={stringifyDate(date)}
    data-value={value}
    on:mouseout={mouseOut}
    on:mouseover={mouseOver}

    style={data && data.hover ? "cursor: pointer;" : false}

    fill={color}
    d={`M${x+radius},${y} h${svgSize} v${svgSize} q0,${radius} -${radius},${radius} h-${svgSize} v-${svgSize} q0,-${radius} ${radius},-${radius}`}
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

$: svgSize = size - (radius)

const getEventData = (event) => {
    return {
        ...data,
        pos: event.target.getBoundingClientRect()
    }
}

const mouseOut = (event) => {
    mouseLeave(getEventData(event));
}
const mouseOver = (event) => {
    mouseEnter(getEventData(event));
}
</script>
