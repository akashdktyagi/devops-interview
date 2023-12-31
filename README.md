# Dev Ops Interview Questions and Sample Answers

### Target Audience: Beginner who wish to give Dev Ops Interviews but have no clue about the set up, work item, day to day activities may look like. 

#### Note: 

* This Questionnaire is written for the students of DevOps/Tech who wish to enter the industry and are keen to know what kind of questions are asked and how the real world enterprise set up may look like. 
* This is off-course not the exhaustive list of questions and the focus is only on the questions which deals with Project, roles and responsibilities etc., day to day activities and how to explain them to interviewers.
* Also the sample answers written below are not to be used exactly how they are written here as they may not be accurate enough in every case. So I recommend please do not mug them up rather frame your own answers based on your experience, Job description and skill set. 
* Feel free to take hints from the sample answers given. 
* If you are an experienced professional who is reading this and find some of the things mentioned here can be made better; then Please propose the changes via Pull request, I will be more than happy to include them for every one’s benifit.



### Question: Tell me about yourself?

#### Suggestions: 
* Include things in which  interviewer would be interested in. 
* There may not be any need include things like your College, College marks (until and unless they are really astonishing). 
* Include things which interviewer can ask more questions from. Give him hints about you want him to ask.

#### Sample Answer: 
* My name is Akash. I am currently working with <Company_Name>. 
* I have (close to) or (number of years) (+) years of work experience in DevOps and  AWS Cloud Computing operations. 
* I am well versed in various AWS managed services like AWS EKS, AWS Beanstalk, AWS Load Balancers, Auto Scaling, lambda, API gateway etc. <Mention your best tools>
* I am expert in tools & Tech like docker, Kubernetes, Terraform, Ansible, Prometheus, Grafana etc.
* I am also very proficient in creating, developing and operation enterprise grade CI CD pipelines using Jenkins (or) Gitlab. <Choose any tool while Answering>
* In my current project I am part of a Dev Ops Team who is handling the day to day Devops operations related to infrastructure and release management. 

### Question: Tell me more about your Project. Or How is your project structured or Tell me how you team works or How many team members your team has or what kind of things your team does?

#### Suggestions: 
* Here the intent is that interviewer is trying to understand your org and team structure. There is no right or wrong answer here. 
* Just to give a general idea, in any company there can be two kind of projects. Either we call it  a vertical project or we call it a horizontal project. 
* A project with a vertical model means they have a dedicated team who only work for that specific project. 
* This kind of teams are mostly individual application or product team which have devs, QA, BA, Product Owner, Scrum master etc. There can 100s of such team in big organisations. In a medium or small company or a start up there can be 10-20 such teams.
* A horizontal project is the project which caters to all the other vertical project who are working on development activities. 
* Example, of such team can be very well your Dev Ops team. Other example, can be Architecture team, InfoSec team, project management teams etc. 
* They all have horizontal function which mean they help all the other product teams (vertical teams) with their specific needs.

#### Sample Answer:  
* My team is structured as horizontal team and we fulfil the DevOps requirement of all the product teams (development teams).
* We cater to primarily three things:
  * Infrastructure provisioning on AWS like VPCs, subnets, Server, k8s
  * Infra Monitoring, Application monitoring using Prometheus Grafana, Alerts
  * Release Orchestration, CI CD onboarding, Security Checks, Compliance, Quality Gates etc
* Our DevOps team is composed of 10 people and divided in to separate sub teams. 
* Out of the three teams we have in our Dev Ops Project, I am working with the CI CD team.


### Question: What are your current roles and responsibilities or What do you do not the daily basis or What kind of work do you do in your project?

#### Suggestions: 
* Modify this based on what is the focus of the Job Description given to you earlier by the interviewer as well as what you know more and comfortable in. 
* Example, CI CD is the most fundamental topic which each Dev Ops engineer must know. If you are a beginner it does not harm to mention this as your current responsibilities. 
* Off-course if you are good in some thing else like AWS or infra and have some experience in that area then mention that instead. If you are confused what to say here, stick with CI CD.

#### Sample Answer: 
* I am currently handling the CI CD pipelines for my project. 
* Our Dev ops team is a horizontal team which caters to all the different product teams in the project. 
* We are responsible for onboarding the projects to our CI CD pipeline which we have built using Gitlab/Jenkins(Choose one, Don’t mention that you use both, If you say both, this may lead to confusion in interviewer’s mind because in enterprise usually they have single tool for CI CD implementation).

### Question: Explain more about your CI CD pipeline, how does it look, what are stages you have?
#### Suggestions: 
* Here the intent is to know about CI CD stages, why do we need CI CD, what problem does it solves? 

#### Sample Answer: 

* When I joined the project there was not much CI CD implementation we had. 
* It was a new project and developers managed to deploy their code manually quickly. But as soon as the number of product teams increased the problem started. 
* Different teams used to manually build, push and deploy their code directly in environments like Dev, SIT and production.
* In the absence of proper CI CD pipeline there were un-necessary delays as well. Our product owners also wanted to embed the security scans directly in to the pipeline.
* To solve all the problems related to build, test, security and deploy our CI CD team was constituted and I joined this team. 
The approach we followed is below:
    1. We analysed how many product team we had in total.  There were around 10 product teams at that time. And we also came to know that it will grow to around 40-50 in few years.
    2. We then planned to create a repository of reusable jobs which can be directly used by individual product pipelines. This is why we implemented re-usability so that we could control every pipeline by directly making changes at just one place.
    3. We created a central repository where we created jobs like, Unit test, Docker Scan, Sonar Scan, Dep Scan, Build, Helm package, Hem Deploy etc. 
    4. Every product team has their own CI CD pipelines but they inherit our central jobs in their pipeline. 
    5. Also, we enforce these compliance framework jobs (these jobs are composed of all the security scan jobs; Gitlab has this concept of Compliance Framework; this can also be done in jenkins btw.)
        1. Note: Compliance Framework is a way of enforcing that each pipeline when triggered, then compliance jobs automatically runs and the product teams can not evade it. This is how we ensure that each app/product pipeline is compliant and code which is being deployed also adheres to complaint norms of the project. 
        2. If we do not have a way of enforcing this, then product team can just comment the compliance jobs in their pipeline and then the compliance framework will not run for their product pipeline. But why would they do this example, removing the compliance jobs execution? There can be many reasons but mostly, when product teams are under pressure to delivery to code feature but do not want to spend time in fixing their docker vulnerabilities or ‘critical” dependence vulnerabilities. Because fixing them requires time which they do not want to invest due to tight deadlines.
        3. However, you being the gatekeeper and touch bearer of making sure the code which is being released is not vulnerable has to make sure that product teams are not able to evade such checks. Hence there are approaches available in almost every pipeline tools to enforce this. In Gitlab we can do this using Compliance Framework. In Jenkins we can implement this using Jenkins Template Engine (a.k.a JTE).


### Question: How many deployment environments do you have?
#### Sample Answer: 
* We have primarily three environments, Dev, SIT, UAT . 
* Then we off course has production environment. 
* So far we do the deployment directly till UAT environment. To deploy to the production environment we need to deploy it manually by manual trigger of the pipeline after manual approval. 
* To summarise we have CI CD pipeline extended till UAT environment only.

### Question: Tell us more about Infrastructure provisioning? 
#### Sample Answer: 
* We have a dedicated team who maintain terraform scripts to provision the infrastructure. 
* Whenever a product team requires a new environment or refresh of existing environment, they raise a request with us via Jira. 
* We have already automated the infra provisioning via Terraform and other scripts. We run them to re-provision, refresh the infra.
* For set up of new infra, we reach out to Architecture team on guidance about the networking, subnets, environments etc.

### Question: How does work come to you? What kind of work do you do on the daily basis?
#### Sample Answer: 
* We have Kanban board and tickets are created directly, once tickets are created there, they are assigned to individual dev ops team based on the nature of work.
<More to be written here>

### Tell me about the challenge which you face on day to day basis or Tell me a recent challenge which you have faced and solved?

### What tools are using and what version?

### Give me the list of all the tool chain you have used?

### How do you keep yourself updated?

### Tell me about your day to day activities.

### How does it look like to work in an agile env?

### Tell us about ur Infrastructure.

### What is an API gateway?

### how many people are using

### what is Ansible?

### keyword and jargons enbing used like kpis, dora metric?


### can we discuss about the tickets that we might get as a devops engineer on day to day basis for different issues.