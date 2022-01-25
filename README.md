**HOWTO change certificate used for jars-signing**

1) Get JKS keystore, provided by Thawte or any other issuer (not self-signed one!)
2) Open new keystore in portecle or any other editor and change name of the alias to 'brady', if needed
3) In portecle change password for the keystore and password for the alias to 'adminmuzli' (the same as in settings.xml file)
4) Put it to src/main/resources folder instead of the out-of-dated keystore (pay attention to its name - it should be the same 'keystore')
5) Change version in pom-file
6) run`mvn clean install`

*Deployment of signed jar to archiva*
1) Add this to `settings.xml`
   
      	<servers>
			<server>
				<id>syseca-releases</id>
				<username>maven</username>
				<password>password-from-</password>
			</server>
    	</servers>

2) run`mvn clean deploy`
3) remove '< servers> < /servers>' section from settings.xml