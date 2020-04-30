# Jmeter
The Apache [JMeter](https://jmeter.apache.org/) application is open source software, Java application designed to load test functional behavior and measure performance.

## Install Jmeter
Download Jmeter from its official site. If using Window, just run the file jmeter.bat to start JMeter in GUI mode.
* Install plugin manager
```bash
# Jmeter help
jmeter -?
# Jmeter proxy enabled
jmeter -H <proxy_server> -P <proxy_port> -u <proxy_user> -a <proxy_password>
# Install plugin manager
https://jmeter-plugins.org/wiki/PluginsManager/
# Add plugin using plugin manager
launch jmeter --> options --> plugins manager --> select plugin --> Apply & Restart jmeter
```

## Create Jmeter test script
To create a test plan for an API, open the jmeter in GUI mode. The different components of JMeter are called Elements. The elements which we are going to configure in this sample test case are:
* Thread Group - Thread Groups is a collection of Threads. Each thread represents one user using the application under test. It simulates one real user request to the server. The controls for a thread group also allow you to set the number of threads for each group.

The actual number of transactions per second depends on your application response time. If you want your test to generate desired TPS rate it's better to consider [Concurrency Thread Group](https://jmeter-plugins.org/wiki/ConcurrencyThreadGroup/) and [Throughout Shaping Timer](https://jmeter-plugins.org/wiki/ThroughputShapingTimer/) combination.

* Samplers - JMeter supports testing HTTP, FTP and many more protocols. In this example, HTTP request sampler is used to request to a web server.

* Listeners - Listeners show the results of the test execution. They can show results in a different format such as a tree, table, graph or log file.

An example of the Jmeter test plan can be found [here](src)

Run the Jmeter script using the cli as shown below.

```bash
# Run the test script using cli & output the result into a file
# -n non gui mode, -t location of jmeter script, -l location of result file
# -o output folder path, -e generate report dashboard after load test
jmeter -n -t Load_Test_Plan.jmx -l D:\TestResults\Load_Test_Result.jtl -e -o D:\TestResults\Dashboard
```
