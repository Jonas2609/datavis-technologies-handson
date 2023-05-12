<script>
  import { scaleLinear, scaleBand } from 'd3-scale';
    // Dimensions
    const width = 600;
    const height = 300;
    const margin = { top: 10, right: 10, bottom: 30, left: 60 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const data = [
      { service: "Netflix", viewers: 2.9 },
      { service: "Amazon Prime Video", viewers: 1.3 },
      { service: "Disney+", viewers: 2.1 },
      { service: "Hulu", viewers: 0.9 },
      { service: "Apple TV", viewers: 1.1 },
      { service: "Rakuten", viewers: 0.4 }
    ];

     // Configure scales
  const xScale = scaleBand()
    .domain(data.map(d => d.service))
    .range([0, innerWidth])
    .padding(0.1);

  const yScale = scaleLinear()
    .domain([0, Math.max(...data.map(d => d.viewers))])
    .range([innerHeight, 0]);

  // Create chart elements
  const bars = data.map(d => {
    return {
      x: xScale(d.service),
      y: yScale(d.viewers),
      height: innerHeight - yScale(d.viewers),
      width: xScale.bandwidth()
    };
  });
  </script>
  
  <!-- setting a viewBox and max-width allows the SVG to shrink but not grow! -->
  <svg viewbox="0 0 {width} {height}" style="max-width: {width}px">
    <g transform={`translate(${margin.left},${margin.top})`}>
      <!-- Draw bars -->
    {#each bars as bar}
    <rect 
      x={bar.x} 
      y={bar.y} 
      height={bar.height} 
      width={bar.width} 
      fill="#2e4a62" />
  {/each}
    </g>
  </svg>
  