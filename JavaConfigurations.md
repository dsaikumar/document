# Java Configurations

###Starting tomcat 6.X in Debug Mode

To start tomcat 6.x in debug mode, follow the instructions

Step 01. Set System environment variables

 1. JPDA_TRANSPORT=dt_socket
 2. JPDA_ADDRESS=8001 (Any other port you like)

Step 02. Start tomcat using catalina.bat jpda start . Make sure that you have restarted the command prompt window after setting environment variables.

> C:\tomcat\bin>catalina.bat jpda start

Step 03. Debug program from the IDE and bind to 8001 (on JPDA_ADDRESS) port.

###Enabling the JMX for tomcat to monitor in VisualVM

In Windows
    
    startup.bat -Dcom.sun.management.jmxremote.port=<your_jmx_port> -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false
    
In Linux
    
    startup.bat -Dcom.sun.management.jmxremote.port=<your_jmx_port> -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false