**These are things I've done outside of my role at SmartBrief**  
#Things that were

###[rundeck.smartbrief.com](http://rundeck.smartbrief.com)  

  - Automates a previously manual process.
  - This process required active attention and ongoing interaction from QA engineer every step of the process.
  - Designed with scale in mind, can be reused for a rebuild of any environment with any number of machines.
  - Handles a few system administration (qa) tasks for us which are scheduled by jenkins.
  - 588 rebuilds in it's current implementation (qa, pqa, & pqa2), previous number before reset (~January 2015) was around 1200 (around 1788 total rebuilds). Each manual deploy took us about 15 - 20 minutes, the automated process can be run from the QA channel with a command to Jenkins Bot.  
    - 1788 rebuilds x 15 minutes = **26820 minutes** or **447 hours** **saved** since I automated the process. (conservative estimate)

###Continuous Integration

  **Bamboo**
  - When I came to SmartBrief we were using Bamboo, but things weren't entirely operational
  - We relied on Mike Murphy writing x's and check marks on the white board to alert tech team of test failures
  - The test suites weren't accurately reporting some test failures, were reporting tests pass because of misconfiguration  
  - When Kevin left I took over continuous integration at SmartBrief and made the migration to jenkins.
  - Bamboo is great, but industry standard for this process is largely Jenkins.
  - We no longer pay for a Bamboo license, or pay for the plugins Bamboo uses.  

  [**jenkins:8080**](http://jenkins:8080)
  - Jenkins is open source, but also backed by CloudBees as an enterprise solution ensuring it's long term support.
  - Community support is unparalleled, if there isn't a plugin for what you want to do, there is plenty of online documentation to make the plugin yourself.
  - When I migrated all tests over to Jenkins, I also turned on some that weren't being run because Kevin didn't have the time to fix them
  - Reports all test statuses at a glance on our TV in the front of the tech dept.

###SonarQube

  - SonarQube is a tool Kevin was working on before he left, it wasn't operational as I think he'd only been looking into it a few weeks before he left.
  - I took Kevin's implementation and improved on it so it works and runs daily.
  - Sonar has been working since April 2015 and does daily measurements of code health. The measurements look at things like code reuse, technical debt, code coverage, and critical/major syntax errors that are known to cause problems in the future, or are bad practice.


###QA Scripts  

  - `hg clone ssh://hg@hg/qa_scripts`  
  - Included in this repository are a handful of BASH scripts to assist in our every day work, or to be applied as glue to keep portions of our deploy or test pipeline working seemlessly.
  - This repository also contains scripts to back up all configuration files of Jenkins, Rundeck, and SonarQube and checks them into version control. This ensures recovery from disaster is quick, scale this entire system out, and keep configuration consistent.
  - Work across several versions of BASH, will work on any server no matter where you drop it.

###Contributions to the Knowledge Base

  - [QA Server List](https://wiki.smartbrief.com/display/qa/QA+Server+List) contains a list of ALL servers in the QA group. We had nothing like this previously, and there were servers that no one knew about until I took the time to hunt them all down, record their purpose and display it in an easily useable form.
  - [Creative Type Specs](https://wiki.smartbrief.com/display/qa/Creative+Type+Specs) contains PDF's of all advertising specs and an attached tar file containing a sample image for each type of cretive type. I discovered through IAS testing that most devs do **not** use images to test creatives, considering a wide majority of our advertisers communicate through our briefs with images, this should be cannon for testing creatives.  
  - [Proposed Changes and Additions to Tech Team Infrastructure](https://wiki.smartbrief.com/display/qa/Proposed+Changes+and+Additions+to+Tech+Team+Infrastructure) was a doc I created a long time ago that has some ideas on where we can improve our software development lifecycle.
  - [Continuous Integration Server (Jenkins)](https://wiki.smartbrief.com/pages/viewpage.action?pageId=58885017) & [SonarQube](https://wiki.smartbrief.com/display/dev/SonarQube) & [Rundeck Notes](https://wiki.smartbrief.com/display/sys/Rundeck+Notes) contains info on the configuration for each tool.
  - [Docker](https://wiki.smartbrief.com/display/qa/Docker) contains some information for someone curious about Docker to checkout and get a quick idea of what Docker is.

#Things that are

Each of the tools, scripts and docs listed above are in working order currently, but that's not to say they're working as well as they should. Each is set up to do the bare minimum without needing frequent attention. I continue today addressing any issues or errors from all of these tools either when I have some down time from my rigorous manual testing schedule, or outside of work. I am occasionally afforded a little time to work on the backlog of issues these things have, but only enough to apply bandaids rather than treat the issue. This amount of time will never be enough to deliver a great solution for the challenges we face, or fully develop the tools that we're currently using. Sonar has a plugin that works with our Java IDE to provide coverage and reuse information to the dev. There is one test that contains a majority of the tests Mike Murphy wrote that cannot run due to long standing issues in the way the test dependencies are loaded. Rundeck has an API that can perform all the functions we need without it's GUI. I have the solution for these challenges, but don't have the time.

#Things that will soon come to pass

Even though what I've accomplished in only a little over a year is impressive, there is a considerable amount of work left to do on current tools, areas I'd like to improve on, and challenges that still don't have solutions.  

**Monitoring/Logging solution**

- I'd like to implement an [ELK Stack](https://www.elastic.co/webinars/introduction-elk-stack) to improve on or replace scrollkeeper as our logging solution. Currently the logs aren't indexed and aren't searchable outside of command line tools. This solution uses elasticsearch which is similar to Splunk. With this we could provide a way for a developer to search and filter logs to debug, or to filter and search logs for investigative purposes. I've done this for my personal blog, and for a friend's business, I'd love to work on one for SmartBrief.

**Containerization**  

- Docker will absolutely be a game changer for SmartBrief if we take advantage of it. I believe our entrypoint into this is move our development process into containers. After which this should eliminate the need for all VMs in the dev environment and eventually all qa VMs. If done properly, this could free up over 50 VMs used for dev and qa. There is a lot more to this, but thats better left for another conversation. After that I believe there are several other places we can benefit from docker, especially in the world of testing, but those will become a little more clear as Docker work continues.

**Ongoing Documentation Maintenence**

- The SmartBrief tech knowledgebase has a considerable amount of docs that have some parts that need updating, some that still need to be written, and some that just need removing. This isn't a one time process but one that must be addressed on a semi-frequent basis. When new people start working at SmartBrief, they are referred to the wiki in a lot of situations, it would be nice if the information we're giving out is reliable and accurate.



## Here is what I want:  

I've been talking about these topics for a long time now, I need SmartBrief to show me it values my work.  

- A change in title - I think either Infrastructure Engineer or Automation Engineer work well, also open to DevOps Engineer but think there is a bigger conversation for a DevOps title. I no longer want to do any manual project testing. Working on IAS alone for almost a year with no break has burned me out on manual testing. IAS is a large undertaking, a project that deals with the very nature of how we monetize our briefs, a project that **should** be worked on by at least 2 people in tandem, a project that has consistently been given stellar QA work, even when facing deadlines, or failing QA environments.

- A change in salary. While I truly appreciate the above standard raise I received in July, I believe I am working above that level and capable of much more. There is also the situation of cost of living to address. Moving to New York has taken away the benefit of free health care. I have free health care currently only because I didn't switch my plan, but to receive medical attention I must travel to Maryland where the doctor allowed by my plan is. In 2016 I will hopefully be able to switch it over because I cannot afford to now, paying for healthcare will cost me over $50 extra a paycheck. Also consider the higher taxes I have to pay in NY, I am now making **less** money than I did when I started working at SmartBrief (by about $100!!) and that includes the raise I've received since.

- A commitment that all infrastructure projects are regarded the same as other projects and given the resources those projects get. I'm not saying I need a dedicated project manager or dedicated devs to work on these projects, I can take on that responsibility, but I cannot do all of this alone all the time and want to know that if I let directors or senior developers know I need help at a specified time in the future, I can get that help.
