# CSU33012 – Software Engineering
## Assignment 3 – Measuring Software Engineering

“From a more abstract point of view, the goal of software measurement is to build and validate hypotheses and increase the body of knowledge about software engineering” (Morasca, n.d.). There isn’t a company in the world who do not evaluate the performance and production of their workers. The use of metrics can allow for management to clearly see how effective a worker has been over a period of time. In some cases, this may be the number of units produced or the number of tables served. However, measuring software engineering is complex in that there may not be a uniform standard for what needs to be measured. The use of normal metric such as these are not applicable to the world of software engineering, where projects can vary between taking place over a number of weeks or months to create large scale applications, to taking place over a single day in order to fix small bugs and errors.

Throughout the course of this paper, I will explore and discuss some of the past and current metrics which are used to measure the work of a software engineer and the complexity of their code, providing an evaluation on the benefits and pitfalls of each. Further to this, I will explore some of the new technologies being used in the industry to measure engineers, from the efficiency to their work ethic, and even their well being.


## Methods of yesteryear

### Counting LOC

Counting the number of lines of code is a method that has been employed for many years but carries with it many flaws. “Source Lines of Code (SLOC or LOC) is one of the most widely used sizing metric in industry and literature” (Nguyen, et.al, 2007). However, there is often confusion regarding what constitutes a “source line of code”.  Measuring engineers on the number of lines of code they write can lead to serious issues of inefficiency, as well as difficult, hard-to-follow "spaghetti code" in larger scale projects. For example:

    if(num%2 == 0)
    {
      print(“Number is Even.”)
    }

is correct and is equivalent to four physical SLOC. However, this simple statement can be simplified down to one physical SLOC:

    if(num%2 ==0) print(“Number is Even.”);

While the two functions perform the same task, the physical number of lines makes the first piece of code less efficient. By measuring software engineers on the number of SLOC in their systems, it promotes the use of inefficient, unnecessarily long code, which, when applied to systems of a massive size, can lead to complications when trying to debug.  Another issue with counting SLOC, especially in the present day with new languages, such as Python, which can perform operations in fewer lines of code, is that programmers will be swayed away from using these more efficient languages. The following piece of code reverses a string in Java, taken from GeeksForGeeks.com, containing twenty physical SLOC.

    // Java program to ReverseString using ByteArray.
    import java.lang.*;
    import java.io.*;
    import java.util.*;
 
    // Class of ReverseString
    class ReverseString {
        public static void main(String[] args)
        {
            String input = "GeeksForGeeks";
 
            // getBytes() method to convert string
            // into bytes[].
            byte[] strAsByteArray = input.getBytes();
 
            byte[] result = new byte[strAsByteArray.length];
 
            // Store result in reverse order into the
            // result byte[]
            for (int i = 0; i < strAsByteArray.length; i++)
            result[i] = strAsByteArray[strAsByteArray.length - i - 1];
 
            System.out.println(new String(result));
        }
    }
    
Meanwhile the same function can be carried in Python Programming Language in a much more efficient way, using only two physical SLOC:

    txt = "GeeksforGeeks"[::-1]
    print(txt)

There are of course tools that exist that aid in the counting of these SLOC. In 2004, there were “at least 75 commercial software cost-estimating tools” (Jones, 2004). Again, however, these tools count the lines, and not the *importance* of the lines written for the programmes. Think for example, of writing the code for accepting payment on an e-commerce site. The code written for this function will most likely be less than that the of the whole site. So, by having the tool say that a particular engineer has written a proportionally small X% of code for the whole store, the code written is an integral piece to the system. 

The counting of code can also be done by counting the number of logical lines of code, that being the lines of code which services a purpose. So, in other words, the number of physical lines of code minus any comments made within the code block. For example, applying this to the above code blocks, the former contains fourteen logical lines of code, while the later still has two logical lines of code. While this would stop software engineers from writing needless comments in order to “bump up” their number of lines, it does still allow for engineers to write long, drawn-out code rather than the much sorter, efficient code that can be used.

### Repository Commits

Another method which has been used before to measure the work of a software engineer is the number of commits they have to their repository of work. Each commit is given a unique ID, using which people can view which changes were made at a given point in time. Many repositories allow for users to see how often commits are made.

![Commits](https://github.com/donneleo/Measuring-Software-Engineering/blob/main/assets/Capture.PNG)

While this, again, can be a reflection of how often the engineer works, or how consistently they commit code into a project, this again is a flawed method of measurement. Any minute change to a piece of code needs to be committed to the repository in order to become a part of the project. So, while an engineer may be committing on a consistent basis, many commits may only be for small spelling errors, rather than meaningful contributions to a project. Tools like Teamfeed exist as well to help track the number of commits a user makes to a repository and gamifies this by making leader boards of who has made the most commits, and sending regular emails to the team members. However, the same negative impacts were observed in a study carried out by Singer and Schneider, 2012, where the student using Teamfeed said that “Just because someone had submitted something to version control, they said, did not mean that there was actually any value in the commit” (Singer & Schneider, 2012). Some of the students even noted how they viewed the emails as spam, and they often went unread. We can evaluate from this that Teamfeed is an ineffective tool.

### Cyclomatic Complexity

In 1976, Thomas McCabe proposed that the metric of cyclomatic complexity be used as a method for evaluating the work of a software engineer and as a “predictor of various software attributes such as reliability and development effort” (Sheppard, 1988). Cyclomatic Complexity offers a quantitative measure of the complexity of source code by counting the number of control paths through a piece of code rather than the SLOC themselves, as it would provide a better measurement of work, and “much more related to the testing effort”. Cyclomatic Complexity is often visualized as a flow chart of nodes and edges, such that the cyclomatic complexity of the code is:

<p align="center"> CC = (e - n) + p. </p>

where:
-	CC = Cyclomatic Complexity
-	e = number of edges
-	n = number of nodes
-	p = number of nodes with exit points, i.e. return statements

So, for example the following code statement:

    def mymethod(x, y)
        r = x
        if x > 5
            r = 5
        end
        if y < 5
            r = y
        end
        r
    end

Would have the following graph:

<p align="center"> <img src="https://github.com/donneleo/Measuring-Software-Engineering/blob/main/assets/graph.PNG" alt="Graph"> </p>
(Atencio, 2012).

From our formula, we can see that this program has a cyclomatic complexity of 3.

While this metric does provide a better reflection than simply counting the SLOC, in my opinion, this metric still shares several of the same pitfalls. By measuring software using this metric, it still encourages software engineers to write overly complex code with many winding clauses. This metric becomes even more complicated once it is applied to inter-function, inter-modular programmes, as there are inconsistencies in how some software engineers compute cyclomatic complexity, where some add together the individual complexities of functions and others count at “purely a module level”. As a result of this, it has been suggested that McCabe’s metric of Cyclomatic Complexity can only accurately be applied within intra-modular functions: “the only possible role for cyclomatic complexity is as an intra-modular complexity metric” (Sheppard, 1988).

Some believe that the irrelevance of measuring metrics is due in large part to how little relevance they have based on industry needs. The irrelevance here is due to two main factors:

**•	Irrelevance of Scope** – Many of the metrics used to measure software “can only ever be applied/computed for small programs, whereas all the reasonable objectives for applying metrics are relevant primarily for large systems” (Fenton & Martin, 2007)

**•	Irrelevance of Content** – The metrics that academics are using to measure software engineering are very often not in line with the metrics used within the industry and are therefore redundant.

So, we can see that why these metrics may have been used in the past, but with the number of issues befalling each one, it is only natural that technology companies have been working on created products that can monitor and evaluate software and software engineers. In recent years, many products have been created to monitor the work, efficiency and general well-being of software engineers. What is particularly interesting across theses new technologies is the emphasis on measuring the software engineer, rather than the software itself. These tools come with a myriad of benefits and faults, as well as having their own ethical dilemmas.

## Devices in Use

### Timeular

Timeular is an example of new technologies being used to measure to the of software engineers. A small, eight-sided dice that sits on the engineers desk, the Timeular device can be set face-down on a particular side which begins a clock, timing how long an engineer has been working on a particular aspect of their job. There are options for answering emails, coding and even taking coffee breaks. Such a device, in theory should prove wonders, as employers or line managers can track exactly for how long their employees have been working and assess them with the aid of this information. However, the device is not without fault. Which brings us to our ethical dilemma. The use of this device can only be successful in a setting where the employee can be trusted to *actually* carry out the task they claim to be working on, rather than setting the device to say they are coding, only to spend the next thirty minutes or so browsing videos on YouTube.

### Humanyze Employee Badge

Another new piece of technology being used to measure software engineers in work is the Humanyze Employee ID badge. This tag which has “two microphones doing real-time voice analysis, and each comes with sensors that follow where you are in the office, with motion detectors to record how much you move.” (Heath, 2016). The device will monitor to whom a worker is talking at any one time as well as monitoring the performance of the engineer. These tags will most likely lead to an increase in compliance and productivity in the workplace, but in a world dominated by GDPR laws, I believe that such intrusive and invasive technology will lead to a drastic decrease in employee satisfaction and the company will have issues trying to retain such an unhappy workforce. 

Ethically, the Humanyze tag appears quite Orwellian, in my opinion. In his novel 1984, George Orwell says that “Big Brother” is always watching, and that there are “always eyes watching you and the voice enveloping you. Asleep or awake, indoors or out of doors, in the bath or bed—no escape. Nothing was your own except the few cubic centimetres in your skull.” (Orwell, 1949). Such technology could be proven dangerous if the data were to be stolen, with voice recordings and locations trackers allowing people to learn private information about the employee. Then Humanyze CEO, Ben Waber, himself admitted that the “Big Brother image is a big obstacle in getting people to adopt the badge concept” (Weller, 2016). He also admitted that the constant recording would be a deterrent saying that “people still need to feel comfortable using them in order for the concept”. 

### Steelcase

The Steelcase office chair is an example of new technologies being used to monitor the health and well-being of software engineers. The chair is filled with sensors which monitor the posture of the employee sitting there. This information is stored and sent to the Steelcase Rise mobile app, which lets the user know how they are distributing their weight, how their posture is and gives the user frequent reminders to stand up and take a movement break. The app gives the employee stretching and breathing exercises. The chair also monitors heart rate, stress levels, breathing habits, and displays them for the user.


This technology is very beneficial to the user, as it can allow them to monitor their health while at work, which makes for a perfectly ethical application. The alerts to take movement breaks is very useful for maintaining a balance of work and movement, something which is even more prevalent now in the wake of a pandemic, where more and more people are working from home at their desks. However, while there has been no case of it happening thus far, my fear of such technology stems from how this health information could be held against an employee. Should the chair monitor consistently high stress levels and poor heart rates, an employer might decide to cut the employee from the firm’s health insurance plan, citing the data gathered by the Steelcase chair. The idea of a chair being able to lead to the loss of health insurance seems almost too impossible to fathom, but when a company decides they would like to cut costs, it is not beyond the realms of possibility. So, while at a surface level, this is a perfectly ethical piece of technology, the future possibilities for how it is used are worrying.

### PluralSight


PluralSight is a tool that monitors software engineers with regard to the number of commits they make to a code base. While I have mentioned early the dangers of using the number of commits as a metric, what sets PluralSight apart is the type of meas-urement it does. In their own words, they note how “counting lines of code is no way to measure your work” (Pluralsight, 2020), which is true when the bulk of your days work could be dedicated to deleting unnecessary, redundant pieces of code. 

PluralSight uses Flow, which evaluates and visualises the impact of each commit to the overall project. As mentioned previously, using commits as a metric encourages engi-neers to make pointless, unnecessary commits, but with Flow, the impact of the com-mit is calculated. When a commit is made, Flow can evaluate whether the commit add-ed new and meaningful progress to the project, whether it was a refactoring of existing code or whether the commit had any impact of significance. 

According to PluralSight’s website, using Flows leads to a “137% increase in codebase impact” as well as a “70% decrease in errors encountered by users” (Pluralsight, 2020). It also has functionalities that allow for teams to plan and evaluate their sprints better so that work can be given out more efficiently. Their website also notes a “20% increase in impact to codebase” and “25% increase in commits per day” from teams using PluralSight technologies.  Clearly, we can see from these that PluralSight does lead to an increase in efficiency, without being as invasive as other technologies like the dystopian Humanyze Employee Identification Badge.



## Bibliography

Morasca, S., n.d. Software Measurement. [pdf] Como: Università dell'Insubria Dipartimento di Scienze Chimiche, Fisiche e Matematiche. Available at: <https://www.uio.no/studier/emner/matnat/ifi/INF5181/h11/undervisningsmateriale/reading-materials/Lecture-06/morasca-handbook.pdf> [Accessed 11 November 2020].

Nguyen, V., Deeds-Rubin, S., Tan, T., Boehm, B., 2007, A SLOC Counting Standard, Center for Systems and Software Engineering University of Southern California, Available at: http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.550.8181&rep=rep1&type=pdf [Accessed 12 November 2020]

C. Jones. Software Project Management Practices: Failure Versus Success©, CrossTalk, The Journal of Defense Software Engineering, October, 2004.

L. Singer and K. Schneider, "It was a bit of a race: Gamification of version control," Games and Software Engineering (GAS), 2012 2nd International Workshop on, Zurich, 2012, pp. 5-8

Sheppard, M., 1988, A Critique of Cyclomatic Complexity as a Software Metric, Soft-ware Engineering Journal. 3. 30-36.

Atencio, L., 2012. Measuring Code Complexity - Dzone Java. [online] dzone.com. Available at: <https://dzone.com/articles/measuring-code-complexity> [Accessed 15 November 2020].

Fenton, N. E., and Martin, N. (1999) "Software metrics: successes, failures and new directions." Journal of Systems and Software 47.2 pp. 149-157.

Heath, T., 2016. This Employee ID Badge Monitors And Listens To You At Work — Except In The Bathroom. [online] The Washington Post. Available at: <https://www.washingtonpost.com/news/business/wp/2016/09/07/this-employee-badge-knows-not-only-where-you-are-but-whether-you-are-talking-to-your-co-workers/> [Accessed 13 November 2020].

Orwell, G.., 1949. 1984. Secker & Warburg, p.29.

Weller, C., 2016. Employees At A Dozen Fortune 500 Companies Wear Digital Badges That Watch And Listen To Their Every Move. [online] Business Insider. Available at: <https://www.businessinsider.com/humanyze-badges-watch-and-listen-employees-2016-10?r=US&IR=T> [Accessed 13 November 2020].

Pluralsight.com. 2020. Data Insights Platform For Software Engineers. [online] Availa-ble at: <https://www.pluralsight.com/product/flow/engineers> [Accessed 17 November 2020].
