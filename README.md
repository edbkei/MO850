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
       

2- Teste
