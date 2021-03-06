# Chicago DevSecOps Meetup 2019-03-06

It's time to launch your new product, but are you confident it's not going to crash and burn once you go-live?

This month, Yello Cloud Infrastructure Engineer, Jason Hernandez, will show you how to use JMeter -- the industry standard load and performance measuring tool. Jason will walk us through some of the JMeter features and plugins he used to simulate web traffic with the goal of understanding performance capabilities of Yello's new Interview Scheduling product.

During our lightning round, Jason Allen, will talk about FedRAMP. If you want to provide products to US government departments with high security requirements, then understanding FedRAMP is a must.

https://www.meetup.com/Chicago-DevSecOps/events/258713146/

#### JMeter Headless Execution

You can execute the demo test script, cdso-test.jmx, using the JMeter CLI and generate a dynamic HTML report automatically. Make sure results.csv and results-report/ do not exist before running or JMeter may throw an error. The HTML reports will be available in the ./results-report directory in this example.

``` 
jmeter -n -t ./cdso-test.jmx -l results.csv -e -o ./results-report/ \
  -Jjmeter.reportgenerator.report_title="Performance Testing" \
  -Jjmeter.reportgenerator.overall_granularity=1000  \
  -Jjmeter.reportgenerator.apdex_satisfied_threshold=500 \
  -Jjmeter.reportgenerator.apdex_tolerated_threshold=2000 \
  -Jjmeter.reportgenerator.exporter.html.series_filter="^(DemoSite-0)(-success|-failure)?$"
```

#### Taurus Example

You can execute a test plan using the Taurus yml file. Be sure to have a working Python environment with bzt PIP package installed first.

```
pip install bzt
```

```
bzt ./quick_taurus_test.yml
```

#### Additional Resources

* https://jmeter.apache.org/
* https://www.blazemeter.com/blog
* https://gettaurus.org/
* https://jmeter-plugins.org/
* https://www.ubik-ingenierie.com/blog/reporting-feature-in-jmeter/



