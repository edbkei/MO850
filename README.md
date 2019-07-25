# MO850 README
1- Configuração para ataque de hacker e contra-medidas no Windows.

   1.1 Java version
   
   c:\Users\xxxx>java -version
   
   java version "1.8.0_221"
   
   Java(TM) SE Runtime Environment (build 1.8.0_221-b11)
   
   Java HotSpot(TM) 64-Bit Server VM (build 25.221-b11, mixed mode)
   
   C:\Users\xxxxx>echo %JAVA_HOME%
   
   C:\Program Files (x86)\Common Files\Oracle\Java\javapath

   C:\Users\xxxxx>echo %JRE_HOME%
   
   C:\Program Files\Java\jre1.8.0_221
   
   
1.2 Install Apache 2.4
   
Fontes: 
   
https://www.apachelounge.com/

https://coreruleset.org/installation/

https://www.modsecurity.org/
   
Unzip Apache24.zip of this github into C:\Apache24

httpd.exe -k install # Só 1 vez.

httpd.exe -k start   # Inicialização do Web server Apache

httpd.exe -k restart # Reinicialização do Web server Apache

httpd.exe -k stop    # Parada do Web server Apache

httpd.exe -t         # Teste de configuração 

1.2.1 Check Instalation of Proxy Reverse

GOTO Apache24 -> conf -> httpd.conf

IfModule proxy_module
   
ProxyPass "/" "http://localhost:8080/"

ProxyPassReverse "/" "http://localhost:8080/"

IfModule

*** This makes possible an external user in a browse to type 

http://localhost:80/WebGoat

Then pass by "Firewall" and goto "intranet" as

http://localhost:8080/WebGoat

*** Note: This examples supposes that WebGoat is up and running

1.2.2 Check Instalation of Mod_security2

ACTION: GOTO directory C:\Apache24 -> bin

RESULT: Exists yajl.dll, pcre.dll, lua52.dll, libcurl.dll, libhttpd.dll, libhttpd.dll

ACTION: GOTO directory C:\Apache24 -> modules

RESULT: Exists mod_proxy.so, mod_proxy_http.so, mod_proxy_http2.so, mod_unique_id.so,

        mod_security2.so, mod_proxy.html.so
        
ACTION: Check file C:\Apache24 -> conf -> http.conf

RESULT:

ServerName localhost:80

LoadModule unique_id_module modules/mod_unique_id.so

LoadModule security2_module modules/mod_security2.so

Include conf/modsecurity.conf

(IfModule security2_module)

#SecRuleEngine DetectionOnly

#SecRuleEngine On

#SecRuleEngine Off

    Include conf/extra/modsecurity.conf
    
Include conf/extra/crs-setup.conf

Include conf/extra/crs-rules/*.conf

(IfModule)

ACTION: Check file C:\Apache24 -> conf -> modsecurity.conf

RESULT: SecRuleEngine DetectionOnly  ==> Atack Injection is perceived but not avoided. It is possible to see in log file.

        Note: In WebGoat, SQL Injection, if you type your last name: Snow' or 'a' = 'a
        
              SQL command SELECT * FROM user_data WHERE last_name = 'Snow' will bring full table, successfully. Firewall not block it.
           
        SecRuleEngine On  ==> Atack Injection is perceived and avoided. It is possible to see in log file.

        Note: In WebGoat, SQL Injection, if you type your last name: Snow' or 'a' = 'a
        
              SQL command SELECT * FROM user_data WHERE last_name = 'Snow' will result in unsuccessful. Firewall blocks sucessfully.

2- Teste
