Download Link: https://assignmentchef.com/product/solved-cis4930-network-cache-event-driven-simulator
<br>
<h1>1.   Description</h1>

In the project you will write an eveeent-driven simulator for a network cache system. You will then run the simulator in several test scenarios, and write a short report to describe your test results.

Figure 1. Network Content Cache

Consider the network system in Fig. 1. It shows an institutional network connected to the wider Internet via an access link. A simplified simulation model is shown in Fig. 2.

<ul>

 <li>There are <em>N </em>files (e.g., web page objects), originally residing in faraway Internet (origin) servers. <em>N </em>is large, e.g., <em>N </em>= 10000.</li>

 <li>The institutional users make requests for the files.</li>

 <li>For the intended objective, there is no need to distinguish the origin servers. You can assume there is a single origin server. Similarly, you can assume there is a single user (see Fig. 2).</li>

 <li>The user makes file requests according to a Poisson process with rate <em>λ </em>requests per second. Each request is for file <em>i </em>with probability <em>p<sub>i</sub></em>.</li>

 <li>We care about the response time, which is the duration from the time of the request till the time the file is received by the user.</li>

 <li>There is a cache server in the institution network. A user request goes to the cache first. If the cache contains the requested file, it transmits the file to the user.</li>

</ul>

1

<ul>

 <li>If the cache does not have the requested file, the request goes to the origin server in the Internet. After the origin server replies with the requested file, the file goes to the cache first and is cached, and then goes to the user.</li>

 <li>File <em>i </em>has a size <em>S<sub>i</sub></em>, which is a sample drawn from a Pareto distribution (heavy tail), <em>F<sub>S</sub></em>, with mean <em>µ </em>(e.g., <em>µ </em>= 1 MB).</li>

 <li>The probability <em>p<sub>i </sub></em>reflects the popularity of file <em>i</em>. The <em>p<sub>i</sub></em>’s are generated as follows. For <em>i </em>= 1<em>,…,N</em>, draw <em>q<sub>i </sub></em>independently from another Pareto distribution, <em>F<sub>p</sub></em>. Let <em>p<sub>i </sub></em>= <em>q<sub>i</sub>/</em><sup>P</sup><em><sub>j </sub>q<sub>j</sub></em>, so that each <em>p<sub>i </sub></em>is a probability.</li>

 <li>Suppose the resource limitation is at the access link in the in-bound direction. Its bandwidth is denoted <em>R<sub>a</sub></em>, which is a constant (e.g., <em>R<sub>a </sub></em>= 15 Mbps). We do not need to model the out-bound bandwidth, since the small request messages do not consume much bandwidth.</li>

 <li>The institution network bandwidth is <em>R<sub>c </sub></em>everywhere, which is a constant (e.g., <em>R<sub>c </sub></em>= 100 or 1000 Mbps).</li>

 <li>In the in-bound direction at the access link, there is a first-in-firstout (FIFO) queue with infinite capacity. The returned files enter the FIFO queue and will be transmitted by the access link in order.</li>

 <li>Assume the propagation time within the institution network is 0.</li>

 <li>The round-trip (propagation) time between the institution network and the origin server is <em>D</em>, which is a random variable with a lognormal distribution.</li>

 <li>If a file <em>i </em>is served from the cache, the response time includes only the transmission time from the cache, which is equal to <em>S<sub>i</sub>/R<sub>c</sub></em>.</li>

 <li>If a file <em>i </em>is not in the cache at the time of a request, the following count towards the response time: the round-trip time in the Internet <em>D</em>, the queueing delay at the FIFO queue, the transmission time at the access link, and the transmission time from the cache.</li>

</ul>

Note that after file <em>i </em>is completely transmitted from the access link, it is immediately cached at the cache server (which may involve replacing some cached files). After an additional time <em>S<sub>i</sub>/R<sub>c</sub></em>, it is received by the user.

<strong>Project Objective: </strong>Evaluate Cache Replacement Policies

<ul>

 <li>The cache storage capacity is <em>C</em>, with.</li>

 <li>Replacement Policies: Oldest First/Least-Popular First; Largest First; some combinations of the above. You are encouraged to do some quick research on other replacement policies and evaluate additional policies. You can even design and evaluate your own replacement policy.</li>

 <li>Performance metric: the average response time experienced by the user.</li>

</ul>

Figure 2. Simulation Model

<strong>Midpoint Deliverable (</strong>5% <strong>of course grade):</strong>

<ul>

 <li>Please upload your current code. All that is needed is about 300 lines of your own part of the code (i.e., not the external packages that you use) that passes compilation. If you have multiple files, pleas zip them.</li>

</ul>

<strong>Final Deliverable (</strong>20% <strong>of course grade):</strong>

<ul>

 <li>Your code.</li>

 <li>A readme file containing: how to compile your code; how to modify the input parameters; how to run your code; how to read the output.</li>

 <li>A sample input file (if that is your input method) or a description in the readme file about how to set the input parameters. This allows the TA to test your code.</li>

</ul>

Note: Your typical simulation run may take a long time, e.g., hours. However, the TA will not be able to wait for that long. Please provide a set of input parameters that takes no more than several minutes for your code to finish its execution.

<ul>

 <li>A short report (2-3 pages) in IEEE paper format (double column, 10 point font size) containing: A section describing any unique aspects about your simulator (if any); a section describing the cache replacement policies you simulated; a section containing the results of the simulation, where you use both text and figures to show your results; and a conclusion section summarizing your findings.</li>

</ul>

For your report, you should simulate <strong>at least two cache replacement policies</strong>. There will be bonus points for additional policies, especially if it is your own design.

You can find templates for IEEE journals or conferences, for example, here:

https://www.ieee.org/conferences/publishing/templates.html

If you have time to learn, it is an opportunity for you to use Latex for editing the report. Latex is great for inputing mathematical symbols and equations. Otherwise, you can use MS Office or similar editors. For generating plots on Linux, gnuplot is great.

<ul>

 <li>A demo video (mp4 file) with input parameters such that it takes no more than several minutes for your code to finish its execution. This is just to show that your code works. For Canvas upload, the demo should not be larger than a few hundred megabytes. Otherwise, please use OneDrive or YouTube and provide a link.</li>

</ul>

<strong>Project Groups:</strong>

<ul>

 <li>The project is ideal as a one-person project.</li>

 <li>It is also fine if you want to work in a team of two persons. In that case, you should find your own team member.</li>

</ul>

<strong>Provided Code and Sample</strong>

<ul>

 <li><strong>splay tree: </strong>I have provided the C implementation of the splay tree, which can be used as the priority queue for your simulator. You can find the files under Files/Project/Code/Splay Tree. There is a readme file describing what the files are and how they are used.</li>

</ul>

If you program in C/C++, you should be able to use that implementation. I believe the implementation is very efficient and it can be used for very large-scale simulation.

If you use another language, you need to find a package that implements a priority queue. It doesn’t have to be a splay tree. Of course, you can always write the code by yourself. The assigned project is not very demanding. A sub-optimal data structure or implementation may work just fine.

<ul>

 <li><strong>A simulator example: </strong>I have provided a complete sample of an event-driven simulator under Files/Project/Sample. The sample shares many similarities with our project. It is written in C. There is a documentation file for it under the Doc sub-folder.</li>

</ul>

The sample is not small. You don’t have to look at it if you know what to do about your project. However, if you have difficulty starting the project, you can learn something from the sample.

<h1>2.   Hints</h1>

<strong>Explore the Parameter Space: </strong>Although the project appears to be confined, the parameter space is quite large. It is expected that you will need to explore the parameter space. Your simulation results will depend on the parameters you use. You should show how the performance depends on the parameters for each cache replacement policy. There is not enough space to report the results for all parameters. Use your intuition about what may be realistic or interesting parameters to consider. Here are some hints.

<ul>

 <li>Think about the in-bound traffic load in response to the out-bound requests. The load is with respect to the capacity of the access link. Think about how to estimate the in-bound traffic rate at the access link based on the request rate <em>λ </em>(and cache miss ratio). In your simulation, you should try the light load, medium load and heavy load scenarios.</li>

 <li>The results may be sensitive to various constants, such as the mean file size, the ratio between <em>R<sub>c </sub></em>and <em>R<sub>a</sub></em>, and the storage capacity <em>C </em>relative to the total size of all the files. You should explore some of these.</li>

 <li>The results will be sensitive to the parameters of the distributions <em>F<sub>S </sub></em>and <em>F<sub>p</sub></em>, particularly the power. A generic Pareto distribution has the form</li>

</ul>

<em>.</em>

For <em>α </em>≤ 1, the mean does not exist. For <em>α &gt; </em>1, the mean is equal to . Therefore, you should consider <em>α &gt; </em>1. The smaller <em>α </em>is, the more heavy tailed the distribution is. Please explore a range of values of <em>α</em>, especially for the file size distribution <em>F<sub>S</sub></em>. For each chosen <em>α</em>, you want to make sure the mean file size is a reasonable value for an intended application (e.g., around 1 MB for web objects). Then, you decide the remaining parameter <em>k</em>.

Side Note: Of course, a more convincing procedure is to collect real data to generate the file size distribution for the actual application, and use that distribution to drive your simulation. However, that procedure also has a drawback, which is that it lacks generalizability, or the ability to explore alternative scenarios. Our model-based study can answer ‘what-if the file size distribution changes to something else’.

<ul>

 <li>Even under a fixed set of parameters, your results may be sensitive to the random samples of <em>S<sub>i </sub></em>and <em>p<sub>i </sub></em>that you draw from <em>F<sub>S </sub></em>and <em>F<sub>p</sub></em>. You will need to experiment with different sets of samples and find the average over the samples.</li>

 <li>We assume that the round-trip time in the Internet, <em>D</em>, has a lognormal distribution. A lognormal distribution requires two parameters, <em>ζ </em>and <em>σ</em>. In your input file, you should provide the mean and standard deviation for the delay <em>D</em>. In your code, you convert those input parameters to the values for <em>ζ </em>and <em>σ</em>. In your simulation, you should use some reasonable values for the mean and standard deviation for the delay <em>D </em>(e.g., mean 500 ms, and standard deviation 400 ms).</li>

</ul>

<strong>About Event Driven Simulation: </strong>In event-driven simulation, events are dynamically generated as the simulation proceeds. Each event has a time of occurrence. Your simulator processes the events in the order of their occurrence times. When processing an event, one or more future events may be generated and scheduled according to their times.

The main thing needed is an efficient data structure that maintains all the outstanding events and allows you to have access to the next event based on the occurrence time. Such a data structure is known as a priority queue. Your simulator’s main loop is to dequeue the next event from the priority queue (which must be the event with the smallest time among all the outstanding events), advance global time to the time of the event just dequeued, and process the event, until (i) the priority queue is empty, (ii) the total number of events reaches a limit, (iii) the global time reaches a limit, or (iv) some other stopping criterion are met.

As an illustration, the priority queue may be as simple as a sorted list that keeps the outstanding events in increasing order of their times. After processing an event on hand, your code removes the first event from the list and processes it. If during the processing, a new event needs to be scheduled to occur at a future time, you insert the new event on the list at the right place based on the time. Of course, a sorted list may not be fast enough, especially for insertion of new events. For large-scale simulation, the priority queue needs to be efficient in terms of the number of operations needed to dequeue an event or insert a new event. Generally, some types of tree structure is used for the priority queue. My sample code in C uses a splay tree. You can do some online research and read about priority queues, splay trees, and other possible implementations of a priority queue. For major languages, there should be either library functions or user implementations of typical priority queues that you can use.

<strong>Events for Our Network Cache Study: </strong>This part is intended to get you started. It may not cover all possible situations.

You keep track the global time with a variable, say, current-time. When you dequeue an event from the priority queue, you advance current-time to the event time. Then, you check the event type and process it accordingly. To illustrate, you may need the following event types.

<ul>

 <li>new-request-event: This event corresponds to a new user request for a file. When processing such an event, the following need to be done.

  <ul>

   <li>check the cache for the file</li>

   <li>if there is a cached copy, generate a new file-received-event, with the event-time = current-time + <em>S<sub>i</sub>/R<sub>c</sub></em>.</li>

   <li>if there isn’t a cached copy, generate a new arrive-at-queue-event, with the event-time = current-time + <em>D</em>, where <em>D </em>is a (fresh) sample drawn from the lognormal distribution.</li>

   <li>generate another new-request-event with the event-time = currenttime + <em>X</em>, where <em>X </em>is a sample drawn from the exponential distribution with parameter <em>λ </em>(i.e., mean 1<em>/λ</em>).</li>

  </ul></li>

 <li>file-received-event: This event represents that a file has been received by the user. When processing such an event, the following need to be done.</li>

</ul>

-calculate the response time associated with that file and record the response time (a data sample has been collected).

<ul>

 <li>arrive-at-queue-event: This event corresponds to a file arriving at the in-bound FIFO queue. When processing such an event, the following need to be done.</li>

</ul>

-if the queue is empty, generate a new depart-queue-event, with the event-time = current-time + <em>S<sub>i</sub>/R<sub>a</sub></em>.

-if the queue is not empty, add the file (i.e., the info about the file) at the end of the FIFO queue.

<ul>

 <li>depart-queue-event: This event represents that the access link has finished the transmission of a file (the identity of which is recorded by the event). When processing such an event, the following need to be done.

  <ul>

   <li>store the new file in the cache if there is enough space. If the cache is full, remove enough files based on your cache replacement policy and store the new file.</li>

   <li>generate a new file-received-event, with the event-time = currenttime + <em>S<sub>i</sub>/R<sub>c</sub></em>.</li>

   <li>If the FIFO queue is not empty, generate a new depart-queue-event for the head-of-queue file, say <em>j</em>, with the event-time = current-time + <em>S<sub>j</sub>/R<sub>a</sub></em>.</li>

  </ul></li>

</ul>

<strong>About Poisson Process: </strong>The sequence of file requests follows a Poisson process with rate <em>λ </em>requests per second. For this project, we only need a few facts about the Poisson process. First, it is a point process in the sense that at any time <em>t</em>, there can be at most one point/event happening at that time. The event in a Poisson process should not be confused with the events in our simulator. For the file request process, an event is a file request.

Now, we can talk about the inter-arrival time of the points/events, which is the interval between two consecutive requests. Let <em>X</em><sub>1 </sub>be the time of the first event/request. For <em>n </em>≥ 2, let <em>X<sub>n </sub></em>be the interval between the <em>n </em>− 1-th and the <em>n</em>-th events. A Poisson process can be defined by the sequence of inter-arrival times, i.e., the random variables <em>X</em><sub>1</sub><em>,X</em><sub>2</sub><em>,…</em>: The <em>X<sub>i</sub></em>’s are IID exponential random variables with parameter <em>λ</em>. The mean of each <em>X<sub>i </sub></em>is 1<em>/λ</em>.

The name ‘Poisson process’ comes from the following. For <em>t </em>≥ 0, let <em>N</em>(<em>t</em>) be the number of events that occurred on the interval [0<em>,t</em>]. Then, for each <em>t</em>, <em>N</em>(<em>t</em>) is a Poisson random variable with mean <em>λt</em>. This is why <em>λ </em>is a rate. The collection of all such random variables, {<em>N</em>(<em>t</em>)}<em><sub>t</sub></em><sub>≥0 </sub>is a Poisson process.

<strong>Programming Language: </strong>You can use any programming language. I will give sample code for the priority queue in C. If you use any other language, please find the code that implements a priority queue, or write your own code for it.

<strong>Random Number Generation: </strong>For major programming languages, there should be library functions or packages that you can use for drawing random samples from typical distribution functions. For instance, in C/C++, you can use the GNU Scientific Library (GSL).

<strong>Relevance of the Model: </strong>The model is not realistic enough with respect to how things work on the Internet. Some of the simplifications or omissions are obvious, such as the consolidation of the origin servers into a single one and the lack of details in the network paths. The absence of reactive control of the traffic source is a deeper issue. In reality, file transfer applications typically use TCP, which allows the traffic sources to automatically adapt to network congestion. A more realistic simulator will need to simulate the behavior of TCP, which will require packet-level simulation as apposed to file-level simulation. Having said that, it is often valuable to study a simplified, abstract model. For instance, doing so may provide a quick way for us to gain insights or understanding about the real system under study.