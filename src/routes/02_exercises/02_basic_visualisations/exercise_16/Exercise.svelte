<script>
  const margin = { top: 5, right: 5, bottom: 5, left: 5 };
  const innerWidth = 60 - margin.left - margin.right;
  const innerHeight = 60 - margin.top - margin.bottom;
</script>

<svg viewBox="0 0 60 60">
  <g transform="translate({margin.left}, {margin.top})">
    <circle cx={innerWidth / 2} cy={innerHeight / 2} r="20" fill="teal" />
  </g>
</svg>

<style>
  svg {
    border: 1px solid black;
    border-radius: 5px;
  }
</style>
