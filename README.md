# mcqq<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
    <style>
        canvas{
            border:1px solid #ccc;
            border-radius: 8%;  
        }
    </style>
</head>
		<input type="text" placeholder="请输入验证码不区分大小写" id="inp">
		<button id="btn">提交</button>
        <canvas width="120" height="40" id="canvas">
        </canvas>
        <script>
        	var ctx=canvas.getContext("2d");
        	zong();
	        canvas.onclick=function(){
	        	ctx.clearRect(0,0,canvas.width,canvas.height);
	        	zong();
	        }
            function zong(){
            	var w=120;
           		var h=40;
            	var ctx=canvas.getContext("2d");
            	function sj(min,max){
                	return  parseInt(Math.random()*(max-min)+min);
	            }
	            function sjys(min,max){
	                var r=sj(min,max);
	                var g=sj(min,max);
	                var b=sj(min,max);
	                return `rgb(${r},${g},${b})`;
	            }
	            var c = '';
	            var a = '';
	            var pool="ABCDEFGHIJKLIMNOPQRSTUVWSYZ1234567890";
	            for(var i=0;i<4;i++){
	                var c=pool[sj(0,pool.length)];
	                var fs=sj(18,40);
	                var deg=sj(-30,30);
	                ctx.font=fs+'px Simhei';
	                ctx.textBaseline="top";
	                ctx.fillStyle=sjys(80,150);
	                ctx.save();
	               	a += c;
	                ctx.translate(30*i+15,15);
	                ctx.rotate(deg*Math.PI/180);
	                ctx.fillText(c,-15+5,-15);
	                ctx.restore();
	                	btn.onclick=function(){
	                		console.log(a);
	                		console.log(inp.value);
	                		if (inp.value==a) {
	                			alert("登录成功");
	                		}else{
	                			alert("验证码输入错误");
	                			ctx.clearRect(0,0,canvas.width,canvas.height);
	                			zong();
	                		}
	                	}
	             
	            }
	            
	            for(var i=0;i<5;i++){
	                ctx.beginPath();
	                ctx.moveTo(sj(0,w),sj(0,h));
	                ctx.lineTo(sj(0,w),sj(0,h));
	                ctx.strokeStyle=sjys(180,230);
	                ctx.closePath();
	                ctx.stroke();
	            }
	            for(var i=0;i<40;i++){
	                ctx.beginPath();
	                ctx.arc(sj(0,w),sj(0,h),1,0,2*Math.PI);
	                ctx.closePath();
	                ctx.fillStyle=sjys(150,200);
	                ctx.fill();
	            }
            }
           
        </script>
</body>
</html>
