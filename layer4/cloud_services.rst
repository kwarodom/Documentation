.. _cloud_services:

Layer 4: Cloud Services
==========================

1. Azure Internet of Things
---------------------------
-Azure IoT Online Learning Path 17Oct2016.pptx
https://drive.google.com/open?id=1mQcaTDK8yfBo0vvWIHpo0XY_pmANkrKp
-Azure IOT solution.pdf
https://drive.google.com/open?id=1mZo6hPzE3prhXgJ05ysEciMLjnQJrPU8

2. Azure Web App
----------------

.. image:: ../img/layer4/azuremap.jpg
   :width: 100%

.. table::
   :widths: auto

========== ======= ==================== ================================================= ===============
No         Run?    Name                 Type                                              Location
========== ======= ==================== ================================================= ===============
1          Y       peahivedev           IoT Hub                                           Southeast Asia
2          N       -                    Stream Analytics job                              Southeast Asia
3          Y       peahiveservicebus    Service Bus                                       Southeast Asia
4          Y       peahivedevstorage    Storage Account                                   Southeast Asia
5          Y       peahivedev2          Azure Database for PostgreSQL server              Southeast Asia
6          Y       peahive_dev_sql      SQL Database                                      Southeast Asia
7          Y       peahivedevsql        SQL Server                                        Southeast Asia
8          Y       peahivedevsql        App Service (mobile backend)                      Southeast Asia
9          Y       peahivebackend3      Application Insights                              Southeast Asia
10         N       -                    Azure cognitive service                           Southeast Asia
11         Y       peahive_devPlan      Machine Learning Studio web service plan          Southeast Asia
12         Y       peahive_dev          Machine Learning Studio workspace                 Southeast Asia
13         Y       HiveServer           App Service plan                                  Southeast Asia
14         Y       peahive_mobile_pysg  Notification Hub                                  Southeast Asia
15         N       -                    Power BI                                          Southeast Asia
16         N       -                    Azure bot framework                               Southeast Asia
17         N       -                    Azure function for real-time update on mobile     Southeast Asia
========== ======= ==================== ================================================= ===============

Use this connection string to connect to Azure SQL peahive_dev_sql

.. code-block:: sql

jdbc:sqlserver://peahivedevsql.database.windows.net:1433;database=peahive_dev_sql;user=peahive@peahivedevsql;password={your_password_here};encrypt=true;trustServerCertificate=false;hostNameInCertificate=*.database.windows.net;loginTimeout=30;

----

.. Note:: Reading Rainbow Tip: Think about the most important events in the story. Be careful not to re-tell the whole story but give enough detail so that the plot makes sense to someone who hasn’t read the book.
