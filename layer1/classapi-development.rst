.. _classapi-development:

ClassAPI Development

Layer 1: Device Connectivity
============

1.1  Device Communication Technologies/Protocols
--------
    PEA Hive Platform ถูกออกแบบให้สามารถรองรับเทคโนโลยีการสื่อสาร และโปรโตคอล ที่หลากหลายไม่ว่าจะเป็นอุปกรณ์ขนาดเล็กที่เป็นเซ็นเซอร์ชนิดต่างๆ ที่ประหยัดพลังงานมักจะใช้การสื่อสาร ที่เป็น  Zigbee หรือ Zwave  กล้องวงจรปิด  มักจะใช้การสื่อสารที่เป็น wifi และ PV inverter และแบตเตอรี่ ที่ใช้ในการกักเก็บพลังงานในบ้านมักจะใช้ Modbus เป็นต้น

    1.1.1 Zigbee
            Zigbee นั้นเริ่มต้นตั้งแต่ปีพ.ศ. 2541 และกลายเป็นมาตรฐานในปี พ.ศ. 2546 ความจริงชื่อของ Zigbee เกิดจากการเต้นรำแบบฮาร์เบียหลังจากที่ผึ้งกลับมาสู่รังผึ้ง Zigbee อ้างว่ายี่ห้อและสินค้าต่างผู้ผลิตก็สามารถทำงานร่วมกันได้  แต่สิ่งหนึ่งที่ต้องระวังก็คือมีผู้ผลิต Zigbee จำนวนมาก  ขณะที่ Z-Wave เป็นกรรมสิทธิ์ของผู้ผลิตชิปเพียงรายเดียวคือ Sigma Systems ดังนั้น Zigbee อาจมีข้อผิดพลาดในการทำงานร่วมกันได้
            ข้อดีของ Zigbee คือผลิตภัณฑ์ Zigbee ส่วนใหญ่จะทำงานร่วมกันได้ อย่างไรก็ตามนี่เป็นเพียงข้อตกลงเท่านั้น เนื่องจากยังคงพบปัญหาด้าน การเชื่อมระหว่างอุปกรณ์ Zigbee อย่างต่อเนื่อง  จำนวนอุปกรณ์ที่รองรับ: Zigbee มีผลิตภัณฑ์มากมายซึ่งรวมถึงยี่ห้อ(Brand) ที่มีชื่อเสียง เช่น Philips, Lutron, Samsung เป็นต้น ราคา: ผลิตภัณฑ์ของ Zigbee ดูเหมือนจะมีราคาที่ไม่แพง เนื่องจากเทคโนโลยีของพวกเขาไม่ได้มีการผูกขาดกรรมสิทธิ์ผู้ผลิตชิปเพียงรายเดียว ระยะทางครอบคลุมช่วงสัญญาน: คล้ายคลึงกับ Z-Wave ระยะทางสามารถขยายได้ จากการที่อุปกรณ์แต่ละตัวสามารถทำหน้าที่เป็นตัวกลางให้กับอุปกรณ์อีกตัวหนึ่งได้ ซึ่ง Zigbee นั้นมีความสามารถในการครอบคลุมพื้นที่ได้ไกลกว่า Z-Wave เนื่องจากจำนวนจุดที่ขยายไปจาก Hun นั้นทำได้ถึง 30 hops เมื่อเทียบกับ 4hops ของ Z-Wave อย่างไรก็ตามกระโดดที่มากขึ้น ก็ทำให้เกิดความล่าช้ามากขึ้นเช่นกัน
            ข้อเสียของ Zigbee คือปัญหาการรบกวนที่อาจเกิดขึ้น: เนื่องจาก Zigbee ใช้งานบนคลื่นความถี่ 2.4GHz ซึ่งเป็นความถี่เดียวกับ WiFi และ Bluetooth ดังนั้นจึงอาจเกิดการรบกวนจากอุปกรณ์อื่นๆ และทำให้เกิดความล่าช้าตามมา การทำงานร่วมกัน: นอกจากข้อดีก็ยังเป็นข้อเสียของ Zigbee อยู่ถึงแม้จะเป็นข้อตกลงให้ทำงานร่วมกันได้แต่กลับไม่มีมาตรการควบคุม ดังนั้นโปรดตรวจสอบให้แน่ใจทุกครั้งเมื่อคุณเลือก Hub หรืออุปกรณ์  อีกทั้งมีผู้ผลิตชิป Zigbee จำนวนมากจึงเป็นเรื่องยากที่จะทราบว่าผลิตภัณฑ์ ใดที่ทำตามมาตรฐาน ของกลุ่มพันธมิตรได้จริง
    1.1.2 Z-Wave
            เทคโนโลยี Z-Wave(ซี-เวฟ) มีต้นกำเนิดมาจากเมืองโคเปนเฮเกนประเทศเดนมาร์กเมื่อปี พ.ศ. 2542 และได้รับการรับรองในสหรัฐอเมริกาเมื่อปี พ.ศ. 2544 ในปีพ.ศ. 2548 กลุ่มผู้ผลิตได้รวมตัวกันเพื่อก่อตั้ง สมาพันธ์ Z-Wave (Z-Wave Alliance) ซึ่งสรุปแนวคิดของพวกเขาคือ “การทำงานร่วมกัน” หมายความว่าไม่ว่าสินค้าจะถูกผลิตจากโรงงาน ยี่ห้อ(Brand)ใด ผลิตขึ้นในปีไหน หรือ ซอฟต์แวร์ (Software) ที่ใช้จะเป็นอะไร ผลิตภัณฑ์ Z-Wave ทั้งหมดจะต้องสื่อสารกันได้ จึงกล่าวได้ว่าผลิตภัณฑ์ Z-Waveทั้งหมดของคุณสามารถเป็นเพื่อนกันได้ โดยไม่คำนึงถึงว่าพวกจะอายุเท่าไหร่หรือมาจากประเทศไหนในโลกก็ตาม
            ข้อดีของ Z-Wave โดยการทำงานร่วมกัน: สำหรับผู้ที่ไม่ได้ยึดติดกับยี่ห้อใดเป็นหลัก (Brand Loyalty) แน่นอนว่าไม่เป็นปัญหากับคุณแค่เพียงตรวจสอบให้แน่ใจว่ว่าผลิตภัณฑ์ ที่คุณเลือกนั้นได้รับการรับรอง Z-Wave แล้ว และการตัดสินค้าที่ไม่ใช่ออกไป จำนวนอุปกรณ์ที่รองรับ: Z-Wave มีผลิตภัณฑ์ที่รองรับกว่า 1,500 รายการ ทำให้คุณเลือกได้หลากหลายปราศจากการรบกวน จากคลื่นความถี่ Wifi / 2.4GHz: คลื่น Z-Wave ทำงานบนคลื่นความถี่วิทยุแยกต่างหาก (908.42 MHz ในสหรัฐอเมริกา) ต่างจาก Zigbee , WiFi และ Bluetooth ซึ่งสามารถลดความล่าช้าที่อาจเกิดขึ้นได้ หากมีความแออัดของคลื่นความถี่ WiFi / 2.4GHz ระยะทางครอบคลุมช่วงสัญญาน: ระยะทางสามารถขยาย ได้จากการที่อุปกรณ์แต่ละตัวสามารถทำหน้าที่เป็นตัวกลางให้กับอุปกรณ์อีกตัวหนึ่งได้  หากว่าอุปกรณ์นั้นอยู่ห่างจาก HUB เกินไป
            ข้อเสียของ Z-Wave ราคา: พูดกันตรงๆ ราคาที่คุณจ่ายสำหรับอุปกรณ์ Z-Wave นั้นอาจมีค่าใช้มากกว่า Zigbee เล็กน้อยและค่อนข้างมากกว่า WiFiแต่สิ่งที่คุณต้องใช้จ่ายก็เพื่อข้อดีข้างต้นที่กล่าวไปแล้วนั่นเองการย้ายไปยังประเทศอื่น: เนื่องจากคลื่นความถี่อุปกรณ์ Z-Wave ในแต่ละประเทศจะแตกต่างกัน ดังนั้นหากคุณย้ายไปยังประเทศใช้คลื่นความถี่อุปกรณ์ Z-Wave ที่แตกต่าง อุปกรณ์นั้นจะไม่สามารถใช้งานได้
    1.1.3 WiFI/LAN
            WiFiได้เป็นส่วนหนึ่งในชีวิตของเราแล้ว และหลายคนไม่สามารถใช้ชีวิตอยู่ได้โดยปราศจากมัน  ไม่ว่าจะเป็น Netflix หรือ Facebook ที่เรานั่งดูบนโซฟาด้วยแล็ปท็อปของเราพูดอย่างจริงจัง WiFi จะมาเป็นตัวกลางสำหรับ Home Automation
            ข้อดีของ WiFiสำหรับ Home Automation ราคา: หนึ่งในข้อดีที่ใหญ่ที่สุด ที่ผมเห็นในการใช้ WiFi สำหรับ Home Automation คือช่วยให้คุณเป็นเจ้าของได้ด้วยงบที่จำกัดจำนวนอุปกรณ์ที่รองรับ: มี Smart Phone (สมาร์ทโฟน)ที่เปิดใช้ WiFi จำนวนมากและเพิ่มขึ้นเรื่อยๆ  และเวลานี้ HUB ที่เป็นเทคโนโลยี Z-Wave หรือ Zigbee ก็ยังมีการพ่วงสัญญาน WiFi มาให้ด้วย
            ข้อเสียของ WiFiสำหรับ Home Automation คือปัญหาการรบกวน ที่อาจเกิดขึ้นเช่นเดียวกับ Zigbeeและ Bluetoothพลังงานต่ำ ที่ทำงานด้วย คลื่นความถี่ 2.4GHz เหมือนกัน  ซึ่งอาจมีปัญหาเรื่องการรบกวนกันของอุปกรณ์  และยิ่งอุปกรณ์มากขึ้นการรบกวนกันก็มากขึ้นตาม  และก่อให้เกิดความล่าช้าตามมา กระหายพลังงาน: แบตเตอรีที่ใช้สำหรับ Smart Homeจะประสบปัญหาแน่นนอน อันเนื่องมาจากธรรมชาติที่ของ WiFi ที่มีกำลังแรงจะนำมาซึ่งปัญหา และความน่ารำคาญที่ต้องคอยเปลี่ยนแบตเตอรี่
    1.1.4 Modbus
            modbus
    1.1.5 Bacnet
            bacnet
    1.1.6 SNMP
	        snmp
    1.1.7 Bluetooth (BLE)
            Bluetooth(บลู-ทูธ) เริ่มต้นขึ้นในปี 2537 โดย Ericsson และขณะนี้ได้รับการบริหารจัดการโดยองค์กรที่ชื่อ “กลุ่มผู้ให้ความสนใจเป็นพิเศษเกี่ยวกับ Bluetooth สำหรับBluetooth พลังงานต่ำ (BLE) ได้รับการพัฒนาในปี 2011 คือสิ่งที่ผมจะกล่าวถึงนี้
            ข้อดีของ Bluetooth พลังงานต่ำประหยัดพลังงาน: เนื่องจากวิธีการทำงานของ Bluetooth พลังงานต่ำ (4.0) เป็นเลิศด้านการประหยัดพลังงานแบตเตอรี่ – ด้วยการที่อยู่ในช่วง Sleep mode จนกว่าจะมีการเริ่มต้นเชื่อมต่อ ราคา: แม้ว่าจะไม่มีข้อมูลจำนวนมาก แต่เนื่องจาก Bluetooth(บลู-ทูธ) มีมานานแล้วและเป็นมาตรฐานที่ได้รับการยอมรับจากผู้ใช้จำนวนมาก จึงนำเสนอผลิตภัณฑ์ที่มีคุณภาพในราคาที่ต่ำกว่าได้ ความสามารถในการทำงานร่วมกันและฮับ (Centralized HUB): เนื่องจากหลายคนมี Router (เราเตอร์) แบบไร้สายแล้วจึงไม่จำเป็นต้องใช้ HUB เฉพาะในบางกรณีเนื่องจากอุปกรณ์เหล่านี้สามารถเชื่อมต่อกับRouter (เราเตอร์)ในบ้านได้โดยตรง
            ข้อเสียของ Bluetooth พลังงานต่ำ ปัญหาการรบกวนที่อาจเกิดขึ้น: เนื่องจาก Bluetooth พลังงานต่ำ ยังทำงานบนความถี่ 2.4GHz จึงยังมีที่ปัญหาการรบกวนและแทรกแซง จำนวนอุปกรณ์ที่รองรับ: แม้ว่า Bluetooth จะได้ใช้งานมาแล้วถึง 22 ปี แต่กับอุตสาหกรรม Home Automation นั้นไม่ได้เป็นตัวเลือกหลักให้กับผู้บริโภค ในขณะนี้ HUB หลายๆรุ่นยังไม่สนับสนุน Bluetooth พลังงานต่ำด้วยซ้ำ อย่างไรก็ตามหากมองการเปลี่ยนแปลง Bluetooth พลังงานต่ำ ยังคงเติบโตขึ้นในอุตสากรรมนี้ ระยะทางครอบคลุมช่วงสัญญาน: เท่าที่ผมรู้ Bluetooth พลังงานต่ำ ไม่มีความสามารถในการสร้างเครือข่ายต่อเนื่องผ่านตัวอุปกรณ์เช่นเดียวกับ Z-Wave และ Zigbee ดังนั้นจึงถูกจำกัด ขอบเขตโดยรวม
    1.1.8 EnOcean

1.2 Device Discovery
--------------
1.3  Compatible Devices
--------
1.4 ClassAPI Development
-----
    อุปกรณ์ที่ PEA HiVE Platform สามารถรองรับการทำงานได้จะถูกสร้างขึ้นเป็น Class_API ซึ่งถูกเขึ้นขึ้นมาด้วยภาษา python 2.7 โดยภายใน Class API มีฟังก์ชั่นการทำงานดังต่อไปนี้
	1. getDeviceModel ภายในฟังก์ชั่นนี้ จะส่งค่าข้อมูลของผลิตภัณฑ์ดังกล่าวออกมา
	2. getDeviceStatus ภายในฟังก์ชั่นนี้ จะส่งค่าข้อมูลสถานะการทำงานดังกล่าวของอุปกรณ์ต่างๆออกมา เช่น อุณภูมิการทำงาน สถานะของอุปกรณ์ เช่น 	ON/OFF เป็นต้น
    3. เป็นฟังก์ชั่นที่ใช้ในการสั่งการ  เช่น สั่งปรับอุณภูมิการทำงาน สั่งปรับสถานะของอุปกรณ์ เช่น 	ON/OFF เป็นต้น
    4. identifyDevice
    โดยตัวอย่างฟังกชั่นการทำงานของ getDeviceModel , getDeviceStatus , setDeviceStatus,  identifyDevice มีดังต่อไปนี้

.. code-block:: python

    Attributes:
	    GET: temp, override, tstate, fstate, t_type_post
	    GET/POST: time=[day, hour, minute], tmode, t_heat, t_cool, fmode, hold
	    POST: energy_led

        temp        	GET          	current temp(deg F)
        override    	GET          	target temp temporary override (0:disabled, 1:enabled)
        tstate      	GET          	HVAC operating state (0:OFF,1:HEAT,2:COOL)
        fstate      	GET          	fan operating state (0:OFF, 1:ON)
        t_type_post
        time        	GET	POST      Thermostat's internal time (day:int,hour:int,minute:int)
        tmode       	GET	POST      Thermostat operating mode (0:OFF,1:HEAT,2:COOL,3:AUTO)
        t_heat      	GET	POST      temporary target heat setpoint (floating point in deg F)
        t_cool      	GET	POST      temporary target
        .cool setpoint (floating point in deg F)
        fmode       	GET	POST      fan operating mode (0:AUTO,1:AUTO/CIRCULATE,2:ON)
        hold        	GET	POST      target temp hold status (0:disabled, 1:enabled)
        energy_led         	POST      energy LED status code (0:OFF,1:Green,2:Yellow,4:Red)

- รูปที่ 1.4-1 ส่วนประกอบของ class_API

.. code-block:: python

    #method1: GET Open the URL and obtain a model number of a device
	def getDeviceModel(self,urlData):
    	deviceModelUrl = urllib2.urlopen(urlData+"/model") #without data argument this is a GET command
    	print(" {0}Agent is querying a model number (status:{1}) please wait ...".format(self.variables.get('type',None), deviceModelUrl.getcode()))
    	if (deviceModelUrl.getcode()==200):
        	deviceModel = self.getDeviceModelJson(deviceModelUrl.read().decode("utf-8"))
        	print(" {} model is {}\n".format(self.variables.get('type',None),deviceModel))
    	else:
        	print(" wrong url for getting a device model number\n")

- รูปที่ 1.4-2 ส่วนประกอบของ  Class_API  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: GET Open the URL and read the data
    def getDeviceStatus(self,urlData):
    	deviceUrl = urllib2.urlopen(urlData)
    	if (deviceUrl.getcode() == 200): #200 means data is get successfully
      	  self.getDeviceStatusJson(deviceUrl.read().decode("utf-8")) #convert string data to JSON object then interpret it
    	else:
        	print (" Received an error from server, cannot retrieve results " + str(deviceUrl.getcode()))

- รูปที่ 1.4-3 ส่วนประกอบของ Class_API  ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    def getDeviceStatusJson(self,data):
    	# Use the json module to load the string data into a dictionary
    	_theJSON = json.loads(data)

        self.set_variable('day',_theJSON["time"]["day"])
        self.set_variable('hour',_theJSON["time"]["hour"])
        self.set_variable('minute',_theJSON["time"]["minute"])
        self.set_variable('temp',_theJSON["temp"])
        self.set_variable('tmode',_theJSON["tmode"])
    	if "t_heat" in _theJSON:
            self.set_variable('t_heat',_theJSON["t_heat"])
    	else:
            self.set_variable('t_cool',_theJSON["t_cool"])
    	self.set_variable('fmode',_theJSON["fmode"])
        self.set_variable('override',_theJSON["override"])
        self.set_variable('hold',_theJSON["hold"])
        self.set_variable('tstate',_theJSON["tstate"])
        self.set_variable('fstate',_theJSON["fstate"])
    	self.set_variable('t_type_post',_theJSON["t_type_post"])

- รูปที่ 1.4-4 ส่วนประกอบของ Class_API  ในฟังก์ชั่น getDeviceStatus ที่เป็น JSON format

.. code-block:: python

    #method3: POST Change thermostat parameters
	def setDeviceStatus(self,urlData,postmsg):
        #Ex. postmsg = {"tmode":1,"t_heat":85})
        if self.isPostmsgValid(postmsg) == True: #check if the data is valid
        	_data = json.dumps(postmsg)
        	_data = _data.encode(encoding='utf_8')
        	_request = urllib2.Request(urlData)
            _request.add_header('Content-Type','application/json')
        	_f = urllib2.urlopen(_request, _data) #when include data this become a POST command
    	else:
            print("The POST message is invalid, check tmode, t_heat, t_cool setting and try again\n")

- รูปที่ 1.4-5 ส่วนประกอบของ Class_API  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: Identify this device (Physically)
	def identifyDevice(self,urlData,idenmsg):
    	_data = json.dumps(idenmsg)
    	_data = _data.encode(encoding='utf_8')
    	_request = urllib2.Request(urlData+"/led")
    	_request.add_header('Content-Type','application/json')
    	_f = urllib2.urlopen(_request, _data) #when include data this become a POST command
    	print(" {0}Agent for {1} is identifying itself by changing LED light to {2} please wait ...".format(self.variables.get('type',None), self.variables.get('model',None), idenmsg))
    	print(" after send a POST request: {}".format(_f.read().decode('utf-8')))

- รูปที่ 1.4-6 ส่วนประกอบของ Class_API  ในฟังก์ชั่น identifyDevice

----
    1.4.1 classAPI_PhilipsHue
    class API อันนี้ใช้สำหรับ Philips Hueโดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
            print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        	print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API  ในฟังก์ชั่น getAllLights

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ PhilipsHue ในฟังก์ชั่น getLightStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
        _body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	_body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ PhilipsHue  ในฟังก์ชั่น setLightAttribute

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ PhilipsHue  ในฟังก์ชั่น setLightStatus

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ PhilipsHue ในฟังก์ชั่น identifyDevice

1.4.2 classAPI_WeMo
    class API อันนี้ใช้สำหรับ Belkin WeMo devicesโดยที่มันรองรับ XML request. classAPI methods โดยที่ class_API นี้สามารถรองรับเฉพาะการสั่งการคำสั่งที่เป็น ON/OFF เท่านั้น

.. code-block:: python

	Attributes:
	Status     GET/POST   Current Device Status 1 or True for ON and  0 or False for OFF

    #method1: GET a model number of a device by XML read
	def getDeviceModel(self):
        WeMoXMLURL=self.get_variable('address')+'/setup.xml'
    	dom=minidom.parse(urllib2.urlopen(WeMoXMLURL))
         deviceModel=dom.getElementsByTagName('modelDescription')[0].firstChild.data
    	return deviceModel

-รูปที่ 1.4.2-1 ส่วนประกอบของ Class_API_Wemo ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: GET device status by XML read
	def getDeviceStatus(self):
    	header = {
        	'Content-Type': 'text/xml; charset="utf-8"',
        	'SOAPACTION': '"urn:Belkin:service:basicevent:1#GetBinaryState"'
    	}
    	body="<?xml version='1.0' encoding='utf-8'?><s:Envelope xmlns:s='http://schemas.xmlsoap.org/soap/envelope/' s:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'><s:Body><u:GetBinaryState xmlns:u='urn:Belkin:service:basicevent:1'></u:GetBinaryState></s:Body></s:Envelope>"
    	controlUrl=self.get_variable('address')+'/upnp/control/basicevent1'
    	response = requests.post(controlUrl, body, headers=header)
        dom=minidom.parseString(response.content)
    self.set_variable('Status',int(dom.getElementsByTagName('BinaryState')[0].firstChild.data))

-รูปที่ 1.4.2-2 ส่วนประกอบของ Class_API_Wemo  ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: POST Change status
	def setDeviceStatus(self, newstatus):
    	header = {
            	'Content-Type': 'text/xml; charset="utf-8"',
            	'SOAPACTION': '"urn:Belkin:service:basicevent:1#SetBinaryState"'
        	}
    	body="<?xml version='1.0' encoding='utf-8'?><s:Envelope xmlns:s='http://schemas.xmlsoap.org/soap/envelope/' s:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'><s:Body><u:SetBinaryState xmlns:u='urn:Belkin:service:basicevent:1'><BinaryState>"+str(int(newstatus))+"</BinaryState></u:SetBinaryState></s:Body></s:Envelope>"
    	controlUrl=self.get_variable('address')+'/upnp/control/basicevent1'
    	response = requests.post(controlUrl, body, headers=header)
    	dom=minidom.parseString(response.content)
    	responsestatus=dom.getElementsByTagName('BinaryState')[0].firstChild.data
    	if responsestatus!='Error':
        self.set_variable('Status',int(responsestatus))

-รูปที่ 1.4.2-3 ส่วนประกอบของ Class_API_Wemo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: Identify Device by Toggling device status twice
	def identifyDevice(self):
    	self.toggleDeviceStatus()
    	self.toggleDeviceStatus()

-รูปที่ 1.4.2-4 ส่วนประกอบของ Class_API_Wemo  ในฟังก์ชั่น identifyDevice

.. code-block:: python

    #method5: GET current status and POST toggled status
	def toggleDeviceStatus(self):
    	self.getDeviceStatus()
    	self.setDeviceStatus(not self.get_variable('Status'))

-รูปที่ 1.4.2-5 ส่วนประกอบของ Class_API_Wemo  ในฟังก์ชั่น toggleDeviceStatus

1.4.3 classAPI_ACSaijo
class API อันนี้ใช้สำหรับ ACSaijoโดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
        	print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API_ACSaijo  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
    print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
    #   _body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	_body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

1.4.9 classAPI_ObivoSW
class API อันนี้ใช้สำหรับ Zigbee สวิตซ์ยี่ห้อ Obivo โดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
    print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        	print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API_ACSaijo  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
#     	_body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	_body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

1.4.10 classAPI_Netatmo_weather
class API อันนี้ใช้สำหรับ Weather Station ยี่ห้อ Netatmo โดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
        print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        	print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API_ACSaijo  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
#     	_body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	_body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

1.4.11 classAPI_Powermeter_etrix
class API อันนี้ใช้สำหรับมิเตอร์ยี่ห้อ Etrix alam โดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
        	print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
        else:
        	print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
    #    	_body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	    _body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	    print(_body)
    	    opener = urllib2.build_opener(urllib2.HTTPHandler)
    	    request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
            request.add_header('Content-Type', 'application/json')
            request.get_method = lambda: 'PUT'
    	    url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

1.4.12 classAPI__Powermeter_smappee
class API อันนี้ใช้สำหรับมิเตอร์ยี่ห้อ Smappee โดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
            print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        	print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API_ACSaijo  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
    #   _body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	_body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

1.4.13 classAPI_Somfy
class API อันนี้ใช้สำหรับม่านยี่ห้อ Somfy โดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
        print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API_ACSaijo  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
                print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
     #  _body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	_body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

1.4.14 classAPI_Sonos
class API อันนี้ใช้สำหรับลำโพงยี่ห้อ Sonos โดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
        print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        	print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API_ACSaijo  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
    #   _body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
        _body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice

1.4.15 classAPI_ST_OpenClose
class API อันนี้ใช้สำหรับเซ็นเซอร์ประตู(Open close)โดยที่มันรองรับ HTTP GET and POST requests. classAPI methods ได้ถูกออกแบบให้ใช้กับ http URL ของ Hue device ตัวอื่นๆอีกด้วยที่มีการส่งด้วย GET/POST data ที่เป็นฟอร์แมทของ JSON

.. code-block:: python

    #method1: Lights discovery
	def getAllLights(self,urlData):
    	getAllLightsUrl = urllib2.Request(urlData+'/lights') #without data argument this is a GET command
    	print(" {0}Agent is performing lights discovery, please wait ...".format(self.variables.get('type',None)))
    	getAllLights = urllib2.urlopen(getAllLightsUrl)
        _theJSON=json.loads(getAllLights.read().decode("utf-8"))
    	for k in _theJSON.keys():
        	print ('light {} is called \"{}\"'.format(k, _theJSON[k]["name"]))
    	if (getAllLights.getcode()==200):
    print(" {} lights have been discovered\n".format(len(_theJSON.keys())))
    	else:
        	print(" wrong url for getting all lights\n")

-รูปที่ 1.4.1-1 ส่วนประกอบของ Class_API_ACSaijo  ในฟังก์ชั่น getDeviceModel

.. code-block:: python

    #method2: get light status
	def getLightStatus(self,urlData,ID):
    	getLightStatusUrl = urllib2.Request(urlData+'/lights/'+str(ID)) #without data argument this is a GET command
    	print(" {0}Agent is querying attributes and state for light {1}, please wait ...".format(self.variables.get('type',None),ID))
    	getLightStatus = urllib2.urlopen(getLightStatusUrl)
        _theJSON=json.loads(getLightStatus.read().decode("utf-8"))
    	if (getLightStatus.getcode()==200):
        	print(" attributes and state of light {}: \n".format(ID))
    	else:
        	print(" wrong url for getting all lights\n")
    	for k in _theJSON.keys():
        	if k == 'state':
            	print ('state:')
            	for kk in _theJSON[k].keys():
                	print (' {}: \"{}\"'.format(kk, _theJSON[k][kk]))
        	else:
            	print ('{}: \"{}\"'.format(k, _theJSON[k]))

-รูปที่ 1.4.1-2 ส่วนประกอบของ Class_API_ ACSaijo ในฟังก์ชั่น getDeviceStatus

.. code-block:: python

    #method3: rename lights
	def setLightAttribute(self,urlData,ID,ATTRIBUTE,NEWNAME):
    #   _body = '{\"{}\": "{}\"}'.format(ATTRIBUTE,NEWNAME) #don't use format here
    	_body = '{\"'+ATTRIBUTE+'\":\"'+NEWNAME+'\"}' #{"name":"Bedroom Light"}
    	print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID), data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-3 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatus

.. code-block:: python

    #method4: set light states
	def setLightStatus(self,urlData,ID,STATE,NEWVALUE):
    	if (STATE == 'alert') | (STATE == 'effect'):
        	_body = '{\"'+STATE+'\":\"'+NEWVALUE+'\"}' #{"name":"Bedroom Light"}
    	else:
        	_body = '{\"'+STATE+'\":'+str(NEWVALUE)+'}' #{"name":"Bedroom Light"}
  	  print(_body)
    	opener = urllib2.build_opener(urllib2.HTTPHandler)
    	request = urllib2.Request(urlData+'/lights/'+str(ID)+'/state', data=_body)
        request.add_header('Content-Type', 'application/json')
        request.get_method = lambda: 'PUT'
    	url = opener.open(request)

-รูปที่ 1.4.1-4 ส่วนประกอบของ Class_API_ ACSaijo  ในฟังก์ชั่น setDeviceStatust

.. code-block:: python

    #method5: Identify this lights (Physically)
    def identifyLight(self,urlData,ID):
        self.setLightStatus(urlData,ID,'on','false')
    	time.sleep(5)
        self.setLightStatus(urlData,ID,'on','true')

-รูปที่ 1.4.1-5 ส่วนประกอบของ Class_API_ ACSaijoในฟังก์ชั่น identifyDevice






































