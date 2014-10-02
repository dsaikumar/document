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
    
    startup.sh -Dcom.sun.management.jmxremote.port=<your_jmx_port> -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false




### To create single file in  FormDataMultiPart Request from jersery client

1. Create FormDataMultiPart
2. Create FormDataContentDisposition
3. Create FormDataBodyPart
4. Set the file name and the form file filed name in FormDataContentDisposition object
5. Set the FormDataContentDisposition object & the file object & its connect type in the FormDataBodyPart
6. Set the FormDataMultiPart body with the FormDataBodyPart prepared object


###Ref

com.sun.jersey.core.header.FormDataContentDisposition
com.sun.jersey.multipart.FormDataBodyPart
com.sun.jersey.multipart.FormDataMultiPart



       FormDataMultiPart form = new FormDataMultiPart();
       FormDataContentDisposition fdcd =     
         FormDataContentDisposition.name("fileData").fileName(uploadFile.getName()).build();
		FormDataBodyPart fdp = new FormDataBodyPart(fdcd, uploadFile, MediaType.MULTIPART_FORM_DATA_TYPE);
		form.bodyPart(fdp);
		try
		{
			response = createWebResource(req).accept(MediaType.APPLICATION_JSON)
					.entity(form, MediaType.MULTIPART_FORM_DATA).post(GenericResponse.class);
		}
