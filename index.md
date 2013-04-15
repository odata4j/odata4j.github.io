---
layout: index
---
### What is OData?
* OData is a standardized protocol for creating and consuming data-centric apis, building on HTTP and REST.  See [odata.org](http://www.odata.org/)

### What is odata4j?
* [odata4j](http://odata4j.org) is a Java framework that implements the OData protocol for both consumers (client-side) and producers (server-side)

### Getting started: Consuming OData
* Download the latest stable [distribution archive](http://code.google.com/p/odata4j/downloads/list)
* Add **odata4j-clientbundle-x.x.jar** from distribution archive to your build path
* Use the [odata4j consumer api](http://odata4j.googlecode.com/git-history/0.7/odata4j-core/doc/javadoc/index.html) to talk to an existing OData service
* For example...

{% highlight java %}
// create consumer instance
String serviceUrl = "http://services.odata.org/OData/OData.svc/";
ODataConsumer consumer = ODataConsumers.create(serviceUrl);

// list category names
for (OEntity category : consumer.getEntities("Categories").execute()) {
  String categoryName = category.getProperty("Name", String.class).getValue();
  System.out.println("Category name: " + categoryName);
}
{% endhighlight %}

### Getting started: Producing OData
* Download the latest stable [distribution archive](http://code.google.com/p/odata4j/downloads/list)
* Add **odata4j-bundle-x.x.jar** from distribution archive to your build path (or **odata4j-nojpabundle-x.x.jar** for a smaller bundle with no JPA support)
* Choose or implement an ODataProducer using the [odata4j producer api](http://odata4j.googlecode.com/git-history/0.7/odata4j-core/doc/javadoc/index.html)
* For example...
  * Use InMemoryProducer to expose POJOs as OData entities using bean properties: [InMemoryProducerExample.java](https://github.com/odata4j/odata4j/blob/0.7/odata4j-examples/src/main/java/org/odata4j/examples/producer/inmemory/InMemoryProducerExample.java)
  * Use JPAProducer to expose an existing JPA 2.0 entity model: [NorthwindJPAProducerExample.java](https://github.com/odata4j/odata4j/blob/0.7/odata4j-examples/src/main/java/org/odata4j/examples/producer/jpa/NorthwindJpaProducerExample.java)
  * Implement the [ODataProducer](http://odata4j.googlecode.com/git-history/0.7/odata4j-core/doc/javadoc/org/odata4j/producer/ODataProducer.html) interface directly
  * Expose AppEngine's Datastore as an OData endpoint: [odata4j-appengine](http://code.google.com/p/odata4j/source/browse?repo=samples&name=0.4#git%2Fodata4j-appengine)
  * Host your producer in Tomcat: <http://code.google.com/p/odata4j/wiki/Tomcat>

### Framework design principles
* Leverage existing Java standards (e.g. [JAX-RS](https://jsr311.dev.java.net/), [JPA](http://jcp.org/en/jsr/detail?id=317), [StAX](http://jcp.org/en/jsr/detail?id=173))
* Utilize a small number of carefully-chosen Java open-source components (e.g. [jersey](https://jersey.dev.java.net/), [Joda Time](http://joda-time.sourceforge.net/))
* Support OData consumers in constrained Java client environments, specifically [Android](http://developer.android.com/index.html)
* Support OData producers in constrained Java server environments, specifically [Google AppEngine](http://code.google.com/appengine/)

### More information
* Licensed under [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)
* [Javadocs](http://odata4j.googlecode.com/git-history/0.7/odata4j-core/doc/javadoc/index.html) for the latest stable release
* Support and discussion on the [odata4j-discuss](http://groups.google.com/group/odata4j-discuss) group
* Feature requests and bug reports tracked on the [issues](http://code.google.com/p/odata4j/issues/list) list
* Contributions welcome - see our [development page](http://code.google.com/p/odata4j/wiki/Development) for details, submit patches via our [review site](http://review.odata4j.org)
