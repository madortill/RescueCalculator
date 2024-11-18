<template>
    <svg xmlns="http://www.w3.org/2000/svg" :viewBox="viewBox" :width="width" :height="height">
      <g id="Layer_1" data-name="Layer 1">
        <rect width="528" height="754" rx="49.97" ry="49.97" />
      </g>
      <g id="Layer_3" data-name="Layer 3">
        <ellipse class="cls-6" cx="203.38" cy="580.21" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="203.49" cy="473.57" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="203.64" cy="369.21" rx="40.29" ry="37.21" />
        <g>
          <ellipse class="cls-6" cx="317.71" cy="369.27" rx="40.29" ry="37.21" />
          <ellipse class="cls-6" cx="317.71" cy="473.57" rx="40.29" ry="37.21" />
          <ellipse class="cls-6" cx="317.71" cy="577.87" rx="40.29" ry="37.21" />
        </g>
        <ellipse class="cls-6" cx="88.29" cy="580.21" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="89.29" cy="473.57" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="89.29" cy="369.33" rx="40.29" ry="37.21" />
        <rect class="cls-6" x="49" y="643" width="178" height="68" rx="28.45" ry="28.45" />
        <ellipse class="cls-6" cx="439.52" cy="677.39" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="317.52" cy="677.39" rx="40.29" ry="37.21" />
        <rect class="cls-5" x="405.21" y="311.79" width="69.57" height="134" rx="28.45" ry="28.45" transform="translate(61.21 818.79) rotate(-90)" />
        <rect class="cls-5" x="405.21" y="513.21" width="69.57" height="134" rx="28.45" ry="28.45" transform="translate(-140.21 1020.21) rotate(-90)" />
        <rect class="cls-5" x="405.21" y="409" width="69.57" height="134" rx="28.45" ry="28.45" transform="translate(-36 916) rotate(-90)" />
      </g>
      <g id="Layer_2" data-name="Layer 2">
        <rect class="cls-1" x="33" y="-33" width="466" height="274" rx="27.62" ry="27.62" />
        <text class="cls-2" transform="translate(100 595)">1</text>
        <text class="cls-2" transform="translate(215 595)">2</text>
        <text class="cls-2" transform="translate(100 490)">4</text>
        <text class="cls-2" transform="translate(330 595)">3</text>
        <text class="cls-2" transform="translate(215 490)">5</text>
        <text class="cls-2" transform="translate(330 490)">6</text>
        <text class="cls-2" transform="translate(100 385)">7</text>
        <text class="cls-2" transform="translate(215 385)">8</text>
        <text class="cls-2" transform="translate(330 385)">9</text>
        <text class="cls-2" transform="translate(100 695)">0</text>
        <text class="cls-4" transform="translate(347 687)">מחק</text>
        <text class="cls-2" transform="translate(450 695)">=</text>
        <text class="cls-3" transform="translate(487 385)">נוסחאות</text>
        <text class="cls-3" transform="translate(495 485)">סוג קרקע</text>
        <text class="cls-3" transform="translate(495 587)">שינוי זוית</text>
      </g>
    </svg>
  </template>
  
  <script>
  export default {
    // name: "SvgComponent",
    props: {
      width: {
        type: String,
        default: "528px",
      },
      height: {
        type: String,
        default: "754px",
      },
      viewBox: {
        type: String,
        default: "0 0 528 754",
      },
    },
  };
  </script>
  
  <style>
  .cls-1 {
    fill: #000000c6;
    opacity: 0.63;
  }
  .cls-2 {
    font-size: 48px;
  }
  .cls-2, .cls-3, .cls-4 {
    fill: #fff;
  }
  .cls-2, .cls-4 {
    font-family: Heebo-Thin, Heebo;
    font-weight: 200;
  }
  .cls-3 {
    font-family: Heebo-Regular, Heebo;
    font-size: 28px;
  }
  .cls-5 {
    fill: #f7931e;
  }
  .cls-4 {
    font-size: 34px;
  }
  .cls-6 {
    fill: #c4c3c2;
  }
</style>