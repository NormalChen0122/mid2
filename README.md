(1) how to setup and run my program <br>
1. 一開始先將uLCD display和B_L4S5I_IOT01A相接，角位如下<br>
serial rx接到D0<br>
serial tx接到D1<br>
reset pin接到D2<br>
5V接到5V<br>
GND接到GND<br>
(注意) 要記得這裡的rx, tx, reset不是看uLCD板子上的，而是線上面的<br>
![image](https://github.com/NormalChen0122/hw3_new/blob/master/hw3_picture/uLCD_pin.jpg)<br>
![image](https://github.com/NormalChen0122/hw3_new/blob/master/hw3_picture/uLCD_pin_mbed.jpg)<br>
![image](https://github.com/NormalChen0122/hw3_new/blob/master/hw3_picture/uLCD_pin_mbed2.jpg)<br>

2. 打開我的手機熱點，等待電腦連到手機的熱點<br>
如果不是要用我的手機熱點而是要用自己的熱點的話，需要做出以下動作:<br>
打開自己的手機熱點，確認電腦連線後，以及VMware選擇bridge的連線方法<br>
接下來在terminal上面打上```ip address```來查看自己的VMware ip address<br>
接下來將在model_deploy的資料夾底下的mbed_app.json裡的SSID and PASSWORD給換成自己的網路熱點設定<br>
接下來將在model_deploy的資料夾底下的main.cpp裡面的```const char* host = "192.168.58.120";```給換成自己的VMware ip address.<br>
接下來將在model_deploy的資料夾底下的wifi_mqtt/mqtt_client.py裡面的```host = "192.168.58.120"```給換成自己的VMware ip address.<br>

3. 接下來就可以將B_L4S5I_IOT01A和notebook給接起來<br>
![image](https://github.com/NormalChen0122/hw3_new/blob/master/hw3_picture/mbed_pc.jpg)<br>
4. 然後輸入此command，將code給燒入B_L4S5I_IOT01A(要注意command裡面的那個ee2405v3那個要看自己的mbed-os-build是在哪個資料夾底下，來去做改變)<br>
```sudo mbed compile --source . --source ~/ee2405v3/mbed-os-build/ -m B_L4S5I_IOT01A -t GCC_ARM --profile tflite.json -f```
5. 待燒入完成後，按下B_L4S5I_IOT01A的reset button(也就是在藍色按鈕旁邊的黑色按鈕)<br>
6. 直到uLCD上面寫說run python code，即可新開一個terminal，輸入下列command<br>
```sudo python3 wifi_mqtt/mqtt_client.py```
7. 並在原本的terminal輸入下列command(注意/dev/ttyACM0可能會更動)<br>
```sudo screen /dev/ttyACM0```
8. 如此程式及需要觀察的視窗都開啟完成，即可開始操作老師所想要我們達成的功能<br>
接下來是講解程式中如何操作，而操作結果的圖則是放在(2) what are the results<br>
9. 一開始會進入到gesture UI mode(LED1會亮)，有40, 50 ,60 ,70, 80五個角度可供選擇<br>
我們可以利用出拳或畫圈來增加選擇br>


(2) what are the results<br>
一開始還沒執行python code的樣子<br>
![image](https://github.com/NormalChen0122/hw3_new/blob/master/hw3_picture/run_python_code.jpg)<br>
