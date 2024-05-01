**Architecture** is fundamentally about the intent behind a software system.

An interesting lesson to learn is that good architecture allows major decisions to be deferred until you have more information.

Good architecture opens up options; it does not close them down. It allows you to experiment with many details without committing to any of them.

A good architecture maximizes the number of decisions that are not made.

Think about that very carefully. It happens frequently enough that when I ask people about the architecture of my system, they might say something like, 'Ah, it’s a Java system; we're using Spring and Oracle.' That is not an architecture; you have not given me an architecture. What you've done is show me all the tools in your toolkit. They haven't described the architecture to me. The architecture should make the choice of tools irrelevant. This means, of course, that we want all of the peripheral elements like the database, frameworks, and user interface to be written as plugins to the use cases. This allows you to unplug them and plug in something else later—if you don't like Oracle, for example, you can plug in a different database.

-Robert C Martin
