#第七章   事件
###7.1 事件种类
######7.1.1 鼠标事件

单一作用于某个元素的事件。


     	<style type="text/css">
			div{
				width: 100px;
				height: 100px;
				background-color: red;
				color: ghostwhite;
				font-size: 14px;
			}
		</style>
	</head>
	<body>
		  <div id="mydiv"></div>
		  <script>
		  	var mydiv = document.getElementById("mydiv");
		  	//点击事件
        //		  	mydiv.onclick = function(){
           //		  		alert("点击事件");
           //		  	}
		  	//双击事件
		  		mydiv.ondblclick = function(){
		  		alert("双击事件");
	  	}
           //鼠标摁下
         	mydiv.onmousedown = function(){
		  		mydiv.innerHTML = "按下事件";
		  	}
           	//鼠标抬起
         	mydiv.onmouseup = function(){
		  		mydiv.innerHTML = "";
		  	}
           		//鼠标移动
           		//需要注意的是只要鼠标移动就触发
          document.onmousemove = function(){
          	console.log("移动了");
          }
         	mydiv.onmousemove = function() {
         		console.log("div");
         	}
           	//鼠标移入
           	//会触发冒泡（从内逐级向外依次触发）
           	mydiv.onmouseover = function(){
           		console.log("移入了")
           	}
            
           	//鼠标移出
          	mydiv.onmouseout = function(){
       		console.log("移出了")
         	}
           //会触发多次，取决于嵌套和鼠标位置
           box.onmouseover = function(){
           	console.log("离开.")
           }
            	
		  </script>

鼠标移入移出情况

（1）第一套移入移出会多次触发

        //鼠标移入
        // mydiv.onmouseover =function(){
        //     console.log('移入了');
        // }
        // mydiv.onmouseover =function(){
        //     console.log('红')
        // }
        //会触发冒泡(从内逐级向外依次触发);
        //会触发多次,取决于嵌套和鼠标位置
        // box.onmouseover =function(){
        //     console.log('蓝')
        // }


        //鼠标移出
        // mydiv.onmouseout =function(){
        //     console.log('离开红')
        // }
        // //会触发冒泡(从内逐级向外依次触发);
        // //会触发多次,取决于嵌套和鼠标位置
        // box.onmouseout =function(){
        //     console.log('离开蓝')
        // }
     
(2)第二套移入移出不会会多次触发

       //鼠标移入
        mydiv.onmouseenter =function(){
            console.log('红')
        }
        //不会进行多次触发
        box.onmouseenter =function(){
            console.log('蓝')
        }

        //鼠标移出
        mydiv.onmouseleave =function(){
            console.log('离开红')
          }

###7.1.2 键盘事件
键盘的按钮按下时会触发onkeydown事件，在函数中的e参数代表是哪一个事件触发的。
 

         document.onkeydown = function（e）{
             alert（“按下”）；
             }

键盘的抬起会触发onkeyup事件，它与onkeydown用法一样。

          document.onkeydup = function（e）{
             alert（“抬起了”）； 
             }

###7.2 Event事件对象
#####7.2.1 Event事件对象的概念
Event 对象代表事件的状态，比如事件在其中发生的元素，键盘按键的状态、鼠标的位置、鼠标按钮的状态等等。

#####7.2.2 Event事件对象产生的时间
当用户单击某个元素的时候,我们给这个元素注册的事件就会触发,该事件的本质就是一个函数,而该函数的形参接收一个event对象.
事件通常与函数结合使用，函数不会在事件发生前被执行！

#####7.2.3 Event事件对象接受方式
通过事件触发时的函数，以参数的形式传递进该函数函数内，不要靠调用传参，也就是说event对象是事件处罚书调用函数的第一个参数。

     document.onclick = function(){
                 alert(1);
        }

#####7.2.4 event对象常用属性
鼠标的坐标值：

     e.clientX 和e.clentY

键盘的值：
     e.keyCode


##### 7.2.5 event的兼容性
event对象根据不同浏览器它的获取是不同的方法，以下是针对获取event对象的兼容性写法。（背会）

	//事件触发时,  	   调用的函数(event)
			document.onclick = function(e){
                //非ie         低版本ie
                var ev = e || window.event;
				console.log(e.clientX);
			}

###7.3 对象事件
#####7.3.1 页面（元素）加载完成后执行事件
 window.onload是等待页面加载完成之后执行函数的内容，当然函数没有重载也就是说window.onload只能写一次。

                //页面加载完成之后执行函数内的代码段
             window.onload = function(){
			var mydiv = document.getElementById("mydiv");
			mydiv.onclick = function(){
				alert(mydiv.tagName);
			}
		}
