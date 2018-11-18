# GraphProject
Implementation of Graph DSL using ANTLR and IntelliJ java tutorial by Mohamed Sanaulla Jun. 05, 13.

### References 
1. https://dzone.com/articles/creating-internal-dsls-java
2. https://dzone.com/articles/creating-external-dsls-using
3. https://medium.com/@charinin/installing-antlr-on-ubuntu-and-intellij-ca282dbfc849
4. http://web.archive.org/web/20180710134244/https://github.com/antlr/antlr4/blob/master/doc/getting-started.md
5. http://tinman.cs.gsu.edu/~raj/4330/sp18/antlr4_intelliJ_windows10.pdf
6. https://github.com/antlr/antlr4/issues/179
7. https://github.com/antlr/intellij-plugin-v4/issues/39

### Steps:
1. Open IntelliJ, create `Java Project` using `1.8.0` jdk
2. Under src, create Class `Graph`, `Edge`, `Vertex`, `GraphBuilder`, `EdgeBuilder`, and `GraphDslSample` from internal DSL tutorial
3. Modify main() in GraphDslSample from `Graph()` to `GraphBuilder.graph()`
4. Right click on GraphDslSample.java, choose Run GraphDslSample.main()
5. From File > Settings ... > Plugins, choose Browse Repositories ... 
6. Search for `ANTLR v4 grammar plugin`, right click and choose download and install. Set Http Proxy Settings... accordingly to download.
7. Restart IntelliJ
8. From https://www.antlr.org/download/antlr-4.7.1-complete.jar, Download Complete antlr 4.7.1 jar.
9. From File > Project Structure > Modules, choose `Dependencies` tab, add new `JARs or directories ...`, search for your downloaded jar directory and choose `antlr-4.7.1-complete.jar`
10. Under src, create class `GraphDslAntlrSample` from external DSL tutorial
11. Under src, create new file `Graph.g4` from external DSL tutorial, notice the extension!
12. Right click on Graph.g4, choose `Generate ANTLR Recognizer`
13. `gen` folder will be generated. Right click on gen, choose `Mark Directory as > Generated Sources Root`
14. Resolve conflict in main() of `GraphDslAntlrSample`, carefully import from `org.antlr.v4.runtime` where needed
15. Under src, create new folder `resources`. Under src > resources, create new file `graph.txt` from `graph.gr` from external DSL tutorial
16. Modify main() in GraphDslAntlrSample.java from `resources/graph.gr` to `resources/graph.txt`
17. Right click on GraphDslAntlrSample.java, choose Run GraphDslAntlrSample.main()

### Optional (windows):
1. Under `C:\` create directory `C:\Javalib`
2. Copy `antlr-4.7.1-complete.jar` to `C:\Javalib`
3. Under `C:\Javalib`, create antlr4.bat, write and save `java org.antlr.v4.Tool %*`
4. Under `C:\Javalib`, create grun.bat, write and save `java org.antlr.v4.gui.TestRig %*`
3. Append PATH `C:\Javalib` to system env variable
4. Append or create CLASSPATH to system env variable `.;C:\Javalib\antlr-4.7.1-complete.jar;%CLASSPATH%`
5. Create file `Hello.g4` in whatever directory  
  `// Define a grammar called Hello`  
  `grammar Hello;`  
  `r  : 'hello' ID ;         // match keyword hello followed by an identifier`  
  `ID : [a-z]+ ;             // match lower-case identifiers`  
  `WS : [ \t\r\n]+ -> skip ; // skip spaces, tabs, newlines`  
6. In same directory of Hello.g4, run `antlr4 Hello.g4`, `javac Hello*.java`
7. `grun Hello r -tree`, while console's waiting for input, write `hello parrt` and press enter key, then press `CTRL+Z` (windows) or `CTRL+D` (unix) and press enter key, output should be `(r hello parrt)`
8. `grun Hello r -gui`, do the same as above, while console's waiting for input, write `hello parrt` and press enter key, then press `CTRL+Z` (`^Z` windows newline) or `CTRL+D` (`^D` unix newline) and press enter key, GUI dialog box should pop up.
