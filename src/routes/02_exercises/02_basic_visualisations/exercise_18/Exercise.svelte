<script>
  import { scaleLinear, scaleLog } from 'd3-scale';
  import {axisBottom} from 'd3-axis';
  import {select} from 'd3-selection';

    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 5, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const values = [2, 4, 6, 7, 9];
    const xScale = scaleLog()
    .domain([1, 9])
    .range([0, innerWidth]);
    const xAxis = axisBottom(xScale);

    function createXAxis(node) {
    const xAxisGenerator = axisBottom(xScale);
    const xAxis = select(node).call(xAxisGenerator);

    // Add x-axis label
    xAxis
      .append('text')
      .attr('class', 'axis-label')
      .attr('x', innerWidth / 2)
      // .attr('y', innerHeight - 5)
      .attr('fill', 'currentColor')
      .attr('text-anchor', 'middle')
      .text('X-axis');
  }


  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
        {#each values as value}
          <circle
          cx={xScale(value)}
          cy={innerHeight / 2}
          r="10"
          fill="red"
        />
        {/each}
    </g>    
    <g use:createXAxis transform="translate({margin.left}, {innerHeight-2*margin.top})"/>
    <!----> <text x={innerWidth / 2 + margin.left} y={innerHeight + margin.top + 1} text-anchor="middle" fill="currentColor">X-axis</text> -->
  </svg>
  