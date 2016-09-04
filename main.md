define(function(require,exports,module){
    var load_imgs=require('load_imgs');
   function main() {
        console.log('全部加载完成,已加载：', loadCount);

        // 游戏结束的标记
        var gameover = false;

        // 创建了显示对象


        // 程序的主循环
        var lastTime = Date.now();
        function loop() {
            // 拿到间隔时间
            var now = Date.now();
            var dt = now - lastTime;
            // 这是为了下一帧做准备
            lastTime = now;

            // 清空屏幕
            ctx.clearRect(0, 0, 800, 600);


            // 更新数据、绘制对象


            // 判断是否进入了特殊状态（游戏结束）

            // 1.撞天花板或者地面
            if (bird.y < 0 || bird.y > 600 - 112) {
                gameover = true;
            }

            // 2.撞管子
            if(ctx.isPointInPath(bird.x,bird.y)){
                gameover = true;
            }
            // 清除这一帧已经绘制过的路径
            ctx.beginPath();


            // 绘制所有的displayObject


            // 递归再次调用自身
            if (!gameover) {
                requestAnimationFrame(loop);
            }
        }

        loop();

    }
    module.exports=main;
})
