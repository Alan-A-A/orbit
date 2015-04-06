---
layout : page
title : "Orbit : Actors"
breadCrumb : "[Orbit](index.html) / [Public Documentation](orbit-public-documentation.html)"
next : "orbit-actor-overview.html"
previous: "orbit-building-orbit.html"
---
{% include JB/setup %}

[Actor Overview](orbit-actor-overview.html) {#Actors-ActorOverview}
----------


[Actor Concepts](orbit-actor-concepts.html) {#Actors-ActorConcepts}
----------


[Actor Tutorials](orbit-actor-tutorials.html) {#Actors-ActorTutorials}
----------


 

**Java Example** 
{% highlight java %}
public interface IHello extends IActor
{
    Task<String> sayHello(String greeting);
}

public class HelloActor extends OrbitActor implements IHello
{
    public Task<String> sayHello(String greeting)
    {
        getLogger().info("Here: " + greeting);
        return Task.fromValue("Hello There");
    }
}

IActor.getReference(IHello.class, "0").sayHello("Meep Meep");
{% endhighlight %}
**Scala Example** 
{% highlight scala %}
trait IHello extends IActor {
  def sayHello(greeting: String): Task[String]
}

class HelloActor extends OrbitActor[AnyRef] with IHello {
  def sayHello(greeting: String): Task[String] = {
    getLogger.info("Here: " + greeting)
    Task.fromValue("Hello There")
  }
}

IActor.getReference(classOf[IHello], "0").sayHello("Meep Meep")
{% endhighlight %}
