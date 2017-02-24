<!-- $theme: default -->
<!-- footer: 12 :: Making Code Fly: Load Testing Web Applications -->
<!-- page_number: true -->

# Making Code Fly: Load Testing Web Applications

## Paul Robinson

--- 

# Agenda

* Why do we care about production performance?
* How do we measure it?
* When should we load test our branches/changes?
* How do we actually test it?
* How do we interpret the results?

---

# A note on what we're not talking about

There are multiple thing we could performance benchmark:

* Background job processing time
* Eventual consistency lag
* Transactional load (people changing things)
* Non-transactional load (people looking at things)

Today we're only going to talk about the last one. In technical terms, `HTTP GET`.

---

# Why do we care?

Every request must reach a service, be processed, a response generated and returned to the client. Whilst a thread of execution is running, no other requests can be processed by that thread.

The time that the thread is blocked determines how many requests an individual application instance can handle per second.

---

# Why do we care?

In other words:

$$
floor(C_t\frac{1000}{\bar{R_m}}) = C_c
$$

In English: an application's capaity to serve requests is equal to 1000 divided by the average response time for each thread, multiplied by the number of threads. If I have 4 container threads, and an average response time of 250ms:

$$
floor(4\frac{1000}{250}) = 16
$$

---

# Why do we care?

Let's suppose we expect an application to handle 30,000 requests a minute, or 500 requests/second. Let's call that our Target capacity, _T_. How many instances do we need?

$$
ceil(\frac{T}{C_c}) = C_n
$$

Working that out:

$$
ceil(\frac{500}{16}) = 32
$$

---

# Why do we care?

A new social campaign is going viral. We know that this evening we will hit 150,000 requests/minute. 2,500 requests/second.

$$
ceil(\frac{2500}{16}) = 157
$$

We ask for 157 instances, right? 

---

# Why do we care?

What do we do if we can't spin up enough slaves for this number of instances?

Reason for that might include:

* Budget
* Ability to get more slaves from AWS
* Resource contention leading to runaway response times
* ...

---

# Why do we care?

If we combine our formulas so far into one formula:

$$
ceil(\frac{T}{floor(C_t\frac{1000}{\bar{R_m}}) }) = C_n
$$

I can reduce the number of instances needed for a given capacity by moving one number: 

$$\bar{R_m}$$

---

# Why do we care?

## Response time is a function of cost, and our ability to operate efficiently

(It's also good for consumers - lower response times have been shown to lead to higher conversion rates).

$$
ceil(\frac{2500}{floor(4\frac{1000}{200}) }) = 125
$$


---

# Why do we care?

* Costs
* CTR/CVR increases

## 50ms has a big impact.

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