Lab 2.3: Create Application
---------------------------

.. warning:: After starting the blueprint in UDF, connect to the BIG-IP Cluster BOS-vBIGIP01.termmarc.com and BOS-vBIGIP02.termmarc.com, make sure the cluster shows **In Sync**.

Connect as **paula** to create a new application, go to *Applications* > *APPLICATIONS*, select the template previously created ``f5-HTTPS-WAF-lb-template-custom1``.

Type in a Name for the application you are creating.

- Application Name: ``site18.example.com``

To help identify this application when you want to use it later, in the Description field, type in a brief description for the application you are creating.

- Description: ``My First Application on F5 Cloud Edition``

Type  the domain of your application (this will be used by the ASM policy to enforce the policy on the domain later on)

- Domain Names: ``site18.example.com``

For Device, select the name of the device you want to deploy this application to. (if the HTTP statistics are not enabled, they can be enabled later on after the application is deployed)

- BIG-IP: Select ``BOS-vBIGIP01.termmarc.com`` and check ``Collect HTTP Statistics``

.. image:: ../pictures/module2/img_module2_lab3_1.png
  :align: center
  :scale: 50%

Determine the objects that you want to deploy in this application.
To omit any of the objects defined in this template, click the  (X) icon that corresponds to that object.
To create additional copies of any of the objects defined in this template, click the  (+) icon that corresponds to that object.

In the example, fill out the Server's IP addresses/ports (nodes) and virtual servers names, IPs and ports.

- Pool Members: ``10.1.20.118`` and ``10.1.20.119``
- Service Port: ``80``

- Name Virtual Server: ``vs_site18.example.com_https``
- Destination Address: ``10.1.10.118``
- Destination Network Mask: ``255.255.255.255``
- Service Port: ``443``

- Name Virtual Server: ``vs_site18.example.com_redirect``
- Destination Address: ``10.1.10.118``
- Destination Network Mask: ``255.255.255.255``
- Service Port: ``80``

.. warning:: If the Application is created on AWS, Destination Address and Network Mask needs to be set to 0.0.0.0

It is good practice to type the Prefix that you want the system to use to make certain that all of the objects created when you deploy an application are uniquely named.
If you want to append this prefix to the names of the objects that this application creates, keep Apply Prefix To Names selected.
Appending the prefix to the objects in this application makes these objects easier to find using search filters.


.. image:: ../pictures/module2/img_module2_lab3_2.png
  :align: center
  :scale: 50%

Then Click on Create (bottom right of the window).
The Application is deployed.

.. image:: ../pictures/module2/img_module2_lab3_3.png
  :align: center
  :scale: 50%

.. note:: In case the Application fails, Larry can go to Applications > Application Deployments

In Paula's Dashboard, she can see her Application.

.. image:: ../pictures/module2/img_module2_lab3_4.png
  :align: center
  :scale: 50%

Click on the Application and check the details (alarms, security enabled, configuration, ...)

.. image:: ../pictures/module2/img_module2_lab3_5.png
  :align: center
  :scale: 50%

.. image:: ../pictures/module2/img_module2_lab3_6.png
  :align: center
  :scale: 50%

.. note:: A traffic generator located on the *Ubuntu Lamp Server* server, is sending good traffic every minutes to the virtual servers.

Paula can update Application Health Alert Rules by clicking on the Health Icon on the top left of the Application Dashboard.

.. image:: ../pictures/module2/img_module2_lab3_7.png
  :align: center
  :scale: 50%

.. image:: ../pictures/module2/img_module2_lab3_8.png
  :align: center
  :scale: 50%