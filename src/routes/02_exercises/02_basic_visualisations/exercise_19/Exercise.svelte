<script>
    import { scaleLinear, scaleOrdinal } from 'd3-scale';
    import { schemeDark2 } from 'd3-scale-chromatic';
    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 20, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const values = [
      { x: 2, y: 1, category: "cat1" },
      { x: 4, y: 2, category: "cat3" },
      { x: 6, y: 1, category: "cat2" },
      { x: 7, y: 3, category: "cat3" },
      { x: 9, y: 1, category: "cat2" }
    ];
    const xScale = scaleLinear()
    .domain([2, 9])
    .range([margin.left,innerWidth-margin.right])

    const yScale = scaleLinear()
    .domain([1, 3])
    .range([margin.bottom, innerHeight-margin.top])

    const colorScale = scaleOrdinal()
      .domain([...new Set(values.map(v => v.category))])
      .range(schemeDark2);
    

  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each values as value}
      <line
        x1={xScale(value.x)}
        y1={innerHeight}
        x2={xScale(value.x)}
        y2={yScale(value.y)}
        stroke="gray"
      />
      <circle
        cx={xScale(value.x)}
        cy={yScale(value.y)}
        r="10"
        fill={colorScale(value.category)}
      />
      <text
        x={xScale(value.x)}
        y={yScale(value.y) - 12}
        text-anchor="middle"
        class="valueLabel"
      >
        {value.y}
      </text>
    {/each}
    </g>
  </svg>
  
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
  </style>
  