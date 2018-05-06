.. _index:

Azure IoT with Python
=====================

.. image:: ../img/python-azure-iot/1.png

1. install python sdk
---------------------

**1.1 check cmake and gcc in env**

cmake –version

gcc –version

------------

**1.2 install A Python SDK for connecting devices to Microsoft Azure IoT services**

https://github.com/Azure/azure-iot-sdk-python

------------

**1.3 git clone --recursive**

https://github.com/Azure/azure-iot-sdk-python.git

.. Note:: *–recursive can clone anathor rapo to folder c @ 3290e56

.. image:: ../img/python-azure-iot/2.png

------------

**1.4 Setup and build at folder**

azure-iot-sdk-python/build_all/linux/

in link

https://github.com/Azure/azure-iot-sdk-python/blob/master/doc/python-devbox-setup.md

.. image:: ../img/python-azure-iot/3.png

------------

2. test publish mqtt
--------------------

**2.1 create IoT hub in AZURE**

.. image:: ../img/python-azure-iot/4.png

------------

**2.2 publish mqtt to Azure**

2.2.1 create iot device in Azure

.. image:: ../img/python-azure-iot/5.png

2.2.2 change code in python sample file

CONNECTION_STRING = “HostName= — — -.azure-

devices.net;DeviceId=CoolingSampleDevice_0925;SharedAccessKey= — —

KlOAujkFakeqs2U46GCHybT — -=”

------------

**2.3 Subscribe mqtt to Azure**

2.3.1. create stream process

2.3.2 create service bus topic,

and add bus topic (name home1)

.. image:: ../img/python-azure-iot/6.png

2.3.3 modify stream process (input, Query,output)

2.3.4 select input with iothub name

.. image:: ../img/python-azure-iot/7.png

2.3.5 Query

.. image:: ../img/python-azure-iot/8.png

2.3.6 Output

add output with Hive02 by select output in servicebus name(Hive02) and topic name(home1)

.. image:: ../img/python-azure-iot/9.png

------------

**2.4 test subscribe data by python**

.. image:: ../img/python-azure-iot/10.png

------------
