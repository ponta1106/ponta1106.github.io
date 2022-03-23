<template>
  <div>
    <canvas id="myCanvas" width="300" height="500" style="background-color: #fff; border-radius: 5%;"></canvas>
  </div>
</template>

<script>
export default {
  data() {
    return {
      brickRowCount: 10,
      brickColumnCount: 3,
      brickWidth: 100,
      brickHeight: 80,
      brickPadding: 0,
      brickOffsetTop: -700,
      brickOffsetLeft: 0,
      bricks: [],
      // コンパイル対策
      imgPath: require('@/assets/colossal_titan.png')
    }
  },
  methods: {
    // 巨人の集団を作成、前進するメソッド
    addOffsetTop() {
      var canvas = document.getElementById('myCanvas');
      var ctx = canvas.getContext('2d');
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      for (var c = 0; c < this.brickColumnCount; c++) {
        this.bricks[c] = [];
        for (var r = 0; r < this.brickRowCount; r++) {
          this.bricks[c][r] = {
            x: 0,
            y: 0,
            status: 1
          };

          if (this.bricks[c][r].status == 1) {
            var brickX = (c * (this.brickWidth + this.brickPadding)) + this.brickOffsetLeft;
            var brickY = (r * (this.brickHeight + this.brickPadding)) + this.brickOffsetTop;
            this.bricks[c][r].x = brickX;
            this.bricks[c][r].y = brickY;

            var img = new Image();
            img.src = this.imgPath;
            ctx.drawImage(img, brickX, brickY, this.brickWidth, this.brickHeight);
          }
        }
      }
      this.brickOffsetTop += 1;
      if (this.brickOffsetTop > 500) {
        this.brickOffsetTop = 0;
      }
      requestAnimationFrame(this.addOffsetTop);
    }
  },
  mounted() {
    requestAnimationFrame(this.addOffsetTop);
  }
}
</script>