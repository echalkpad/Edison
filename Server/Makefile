PKG_DIR		=	$(HOME)/Golgi-Pkg/LATEST

JDK_BIN		=	/usr/bin/
JRE_BIN		=	/usr/bin/

JAVA		=	$(JRE_BIN)/java
CLASSPATH	=	$(PKG_DIR)/common/garrick_combined.jar:$(PKG_DIR)/common/golgi_j2se.jar:$(JUNIT_JAR)

all:
	$(JAVA) -classpath $(CLASSPATH) com.openmindnetworks.golgi.garrick.Garrick -i ../GolgiEdison.thrift  -jsf GolgiEdison.js
	cat GolgiForNode.js GolgiEdison.js intel-edison.js > GolgiController.js
clean:
	@find . -name '*.js' | while read f; do if [ `head -2 $$f | egrep -c "IS_AUTOGENERATED_SO_ALLOW_AUTODELETE=YES"` = "1" ]; then echo "Delete $$f"; rm -f $$f; fi; done
run:
	node GolgiController.js -devKey `cat ../Golgi.DevKey` -appKey `cat ../Golgi.AppKey`

