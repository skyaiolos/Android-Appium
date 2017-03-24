

安卓自动化测试：环境的准备：

在做安卓自动化测试之前，需要在你的电脑上做如下环境的准备，
我用的是 Appium做的自动化测试。

 * 安装Appium server， 安装路径：http://appium.io/    https://bitbucket.org/appium/appium.app/downloads/ 
 * Appium 需要 Node JS，所以需要安装它，安装路径：https://nodejs.org/en/ 安装完后，
     可以打开CMD，输入 node –v，如果能显示出 node的version，证明安装成功。


1，2 安装好以后，可以打开 Appium，然后 start 它，如下图：




 安装 Java JDK (安卓是基于java 开发的)， 安装路径：http://www.oracle.com/technetwork/java/javase/downloads/index.html
     


 

安装完后，需要配置环境变量




 
  
  
   
    JAVA_HOME
   
  
  
  
  C:\Program Files\Java\jdk1.8.0_101 (安装路径)
  
 
 
  
  
   
    CLASSPATH
   
  
  
  
  .;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
  
 
 
  
  
   
    Path +
   
  
  
  
  %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
  
 




 



(Eclipse: http://www.eclipse.org/downloads/eclipse-packages/ )

 


 安装 Android SDK， 安装路径：https://developer.android.com/studio/index.html?gclid=CjwKEAjwmMS-BRCm5dn51JLbp1wSJACc61tFag0ZqtZdGSydOBbWbC1TKrebc1z_tn6qQtBq5lJE0BoCNdDw_wcB
     


安装完后同样需要配置环境变量：




 
  
  
   
    ANDROID_HOME
   
  
  
  
  E:\Development\Android\android-sdk (安装路径)
  
 
 
  
  
   
    Path +
   
  
  
  
  %ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;
  
 




 


 打开 Android SDK 安装路径，SDK Manager.exe，打开它，对 Android SDK 做更新，选中需要更新的tool，点金 Install packages





 配置 Android 模拟器: 打开Android SDK 安装路径， 找到 AVD Manager.exe，，打开它，点击 Create，然后创建模拟器 (选择 Device， Target，CPU…)




 

http://www.cnblogs.com/fnng/p/4560298.html

 

因为新虚拟机没了实体键，所以我们可以利用键盘按键来操作android虚拟机。

 




 
  
  模拟器按键
  
  
  键盘按键
  
 
 
  
  后退
  
  
  ESC
  
 
 
  
  菜单
  
  
  F1或Page Up
  
 
 
  
  开始 
  
  
  F2或Page Down
  
 
 
  
   呼叫
  
  
  F3
  
 
 
  
   挂断 
  
  
  F4
  
 
 
  
  电源按钮
  
  
  F7
  
 
 
  
  禁止/启用所有网络
  
  
  F8
  
 
 
  
  开始跟踪
  
  
  F9
  
 
 
  
  停止跟踪
  
  
  F10
  
 
 
  
  旋转屏幕（横/竖屏切换）
  
  
  Ctrl+F11
  
 
 
  
  主页
  
  
  HOME
  
 
 
  
  方向键 左/上/右/下
  
  
  小键盘 4/8/6/2
  
 
 
  
  方向键 中心键
  
  
  小键盘 5
  
 
 
  
  调低音量
  
  
  小键盘 负号(-)
  
 
 
  
  调高音量
  
  
  小键盘 加号(+)
  
 




 


 一切准备就绪之后，打开 VS，然后安装如下 package 


打开 Tools -> NeGet Package manager ->
package manage console

Install-Package Appium.WebDriver

Install-Package Selenium.WebDriver

Install-Package Selenium.Support

Install-Package Newtonsoft.Json

 

接下来就可以写 automation test case了。 

 

其中几个重要的 adb命令：


 adb devices    --- 例举出所有的device
 adb install <path_to_apk>    --安装package到device
 adb push <本地路径><远程路径>   ---从电脑上复制文件到 device
 adb pull <远程路径><本地路径>    ---从device上复制文件到电脑上
 adb shell   --查看文件


 

Using CMD to create environment


 Install Appium server,
     install path: http://appium.io/
     
 Install the Node JS, install
     path: https://nodejs.org/en/ 
 Open the Appium server
 Start the Appium server
 Install the Java JDK, install
     path: http://www.oracle.com/technetwork/java/javase/downloads/index.html
 Install the Android SDK,
     install path: https://developer.android.com/studio/index.html?gclid=CjwKEAjwmMS-BRCm5dn51JLbp1wSJACc61tFag0ZqtZdGSydOBbWbC1TKrebc1z_tn6qQtBq5lJE0BoCNdDw_wcB
     
 Add environment variables for
     Java and Android SDK, like the below screen shot:





 Create Android emulator
 Start emulator
 Install the PowerApp sdk
 Run PowerApp test cases


 

We
can execute the below CMD to create the
above step at WTT:

The
step 1,2,5,6, we can copy the files and install it.

The
step 3, CMD: “C:\Program
Files (x86)\Appium\Appium.exe"   

The
step 4: CMD: “C:\Program
Files (x86)\Appium\node_modules\.bin\appium.cmd” -a 127.0.0.1 -p 4723

The
step 7: we can change the registry value, see the below screen shot:



The
step 8: CMD: android
create avd -n EmulatorName -t 7 -b default/x86   
(details, please refer to: http://blog.sina.com.cn/s/blog_4d353ac3010186c4.html)

The
step 9: CMD: emulator -avd
avdName   (go to the Android SDK tools path firstly)

The
step 10: CMD: adb install
***.sdk

 

 

