<!-- $theme: default -->
<!-- footer: 12 :: Making Code Fly: Load Testing Web Applications -->
<!-- page_number: true -->

# Making Code Fly: Load Testing Web Applications

## Paul Robinson

--- 

# Agenda

* Why do we care about application performance?
* What can we measure?
* How do we measure it?
* When should we load test our branches/changes?
* How do we actually test it?
* How do we interpret the results?

---

# What can we measure?

There are multiple things we could performance benchmark:

* Background job processing time
* Eventual consistency lag
* Transactional load (people changing things)
* Non-transactional load (people looking at things)

---

# Why do we care?

Every request must reach a service, be processed, a response generated and returned to the client. Whilst a thread of execution is running, no other requests can be processed by that thread.

The time that the thread is blocked determines how many requests an individual thread can service.

---

# Why do we care?

In other words:

$$
floor(NumThreads\frac{1000}{Avg Resp Ms}) = Capacity
$$

---

# Why do we care?

Let's suppose we expect an application to handle a target capacity. How many instances do we need?

$$
ceil(\frac{TargetRequests}{Capacity}) = NumAppInstances
$$

---

# Why do we care?

What do we do if we can't spin up enough instances?

Reason for that might include:

* Budget
* Ability to get more slaves from AWS
* Resource contention leading to runaway response times
* ...

---

# Why do we care?

If we combine our formulas so far into one formula:

$$
ceil(\frac{TargetRequests}{floor(NumThreads\frac{1000}{AvgRespMs}) }) = NumAppInstances
$$

I can reduce the number of instances needed for a given capacity by moving one number: 

$$AvgRespMs$$

---

# Why do we care?

## Response time is a contributor to cost, and our ability to respond to demand

It's also good for consumers - lower response times have been shown to lead to higher conversion rates and return rates.

---

# Asynchronous work

Asynchronous/background workers normally work down a queue. Therefore another choice is open to us:

**Don't scale. Just accept queues will grow and work down eventually**

How do you know if this is acceptable?

$$
\frac{JobsAddedPer}{JobsProcessedPer} = AvergageGrowth
$$

If this number is > 1.0, your queue will only ever grow and __you are in a death spiral__.

--- 

# How do we measure it?

For consumer-facing, non-transactional load:

* New Relic is a good start
* We can bake in metrics to go to statsd or Datadog
* Many other alternatives.

---

# How do we measure it?

There are however, downstream dependencies.

* Persistent data stores
* Cache servers
* Other applications (fan-out architecture)

---

# When should we test our changes?

In an ideal world, every branch would be performance tested.

Good candidates for manual testing:

* Your code will be called frequently
* Your code is making more use of an external resource
* You suspect what you're doing will slow it down
* You aren't sure of the answers to the above so want some confidence

---

# When should we test our changes?

Even if you don't test code in advance, you should be checking your metrics daily and comparing with past performance. 

Any degradation should be communicated and mitigated quickly.

If you have request/response cycles regularly taking > 50ms you can argue you have broken code.

---

# How do we actually test changes?

There are three tools in our armoury:

1. Flood.io
2. Sampling GA data
3. QA environments and Staging environments

---

# How do we interpret the results?