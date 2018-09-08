all:
	if [ ! -d classes ] ; then \
	    mkdir classes; \
	fi
	javac -d classes src/test/TestClass.java
	if [ ! -d build ] ; then \
	    mkdir build; \
	fi
	jar cvfe build/a.jar test/TestClass -C classes test 
	cat build/a.jar | jar -t
	java -jar build/a.jar

clean:
	rm -rf ./build ./classes





