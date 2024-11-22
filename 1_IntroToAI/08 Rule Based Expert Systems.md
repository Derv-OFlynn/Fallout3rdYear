### <mark style="background: #69E7E4;">Introduction, or what is knowledge?</mark>

<mark style="background: #69E7E4;">Knowledge</mark> is a theoretical or practical understanding of a subject or a domain.

Knowledge is also the sum of what is currently known, and apparently knowledge is power. Those who possess knowledge are called experts.

Anyone can be considered a <mark style="background: #69E7E4;">domain expert</mark> if he or she has deep knowledge (of both facts and rules) and strong practical experience in a particular domain. The area of the domain may be limited. In general, an expert is a skilful person who can do things other people cannot.

The human mental process is internal, and it is too complex to be represented as an algorithm.

However, most experts are capable of expressing their knowledge in the form of rules for problem solving.

![](https://i.imgur.com/VFKRSkO.png)

### <mark style="background: #69E7E4;">Rules as a knowledge representation technique:</mark>

The term <mark style="background: #69E7E4;">rule</mark> in AI, which is the most commonly used type of knowledge representation, can be defined as an IF-THEN structure that relates given information or facts in the IF part to some action in the THEN part. A rule provides some description of how to solve a problem. Rules are relatively easy to create and understand.

Any rule consists of two parts: the IF part, called the <mark style="background: #69E7E4;">antecedent</mark> (<mark style="background: #69E7E4;">premise</mark> or <mark style="background: #69E7E4;">condition</mark>) and the THEN part called the <mark style="background: #69E7E4;">consequent</mark> (<mark style="background: #69E7E4;">conclusion</mark> or <mark style="background: #69E7E4;">action</mark>).

![](https://i.imgur.com/RV8CYq2.png)

A rule can have multiple antecedents joined by the keywords AND (conjunction), OR (disjunction) or a combination of both.

![](https://i.imgur.com/JbptPuk.png)

The antecedent of a rule incorporates two parts: an object (linguistic object) and its value. The object and its value are linked by an operator.

The operator identifies the object and assigns the value. Operators such as is, are, is not, are not are used to assign a symbolic value to a linguistic object.

Expert systems can also use mathematical operators to define an object as numerical and assign it to the numerical value.

![](https://i.imgur.com/yPvsckm.png)

### <mark style="background: #69E7E4;">Rules can represent relations, recommendations, directives, strategies and heuristics:</mark>

<mark style="background: #69E7E4;">Relation:</mark>
![](https://i.imgur.com/qJytbMk.png)

<mark style="background: #69E7E4;">Recommendation:</mark>
![](https://i.imgur.com/WSgVubv.png)

<mark style="background: #69E7E4;">Directive:</mark>
![](https://i.imgur.com/BRydx12.png)

<mark style="background: #69E7E4;">Strategy:</mark>
![](https://i.imgur.com/j6QJ6wh.png)

<mark style="background: #69E7E4;">Heuristic:</mark>
![](https://i.imgur.com/DFwm3ac.png)

### <mark style="background: #69E7E4;">The main players in the development team:</mark>

There are five members of the expert system development team: the <mark style="background: #69E7E4;">domain expert</mark>, the <mark style="background: #69E7E4;">knowledge engineer</mark>, the <mark style="background: #69E7E4;">programmer</mark>, the <mark style="background: #69E7E4;">project manager</mark> and the <mark style="background: #69E7E4;">end-user</mark>.

The success of their expert system entirely depends on how well the members work together.

![](https://i.imgur.com/W7Ma6KI.png)

<mark style="background: #69E7E4;">Domain Expert:</mark>
- The <mark style="background: #69E7E4;">domain expert</mark> is a knowledgeable and skilled person capable of solving problems in a specific area or <mark style="background: #69E7E4;">domain</mark>. 
- This person has the greatest expertise in a given domain. 
- This expertise is to be captured in the expert system. 
- Therefore, the expert must be able to communicate his or her knowledge, be willing to participate in the expert system development and commit a substantial amount of time to the project. 
- The domain expert is the most important player in the expert system development team.

<mark style="background: #69E7E4;">The knowledge engineer:</mark>
- The <mark style="background: #69E7E4;">knowledge engineer</mark> is someone who is capable of designing, building and testing an expert system.
- He or she interviews the domain expert to find out how a particular problem is solved. 
- The knowledge engineer establishes what reasoning methods the expert uses to handle facts and rules and decides how to represent them in the expert system. 
- The knowledge engineer then chooses some development software or an expert system shell, or looks at programming languages for encoding the knowledge.
- And finally, the knowledge engineer is responsible for testing, revising and integrating the expert system into the workplace.

<mark style="background: #69E7E4;">The programmer:</mark>
- The programmer is the person responsible for the actual programming, describing the domain knowledge in terms that a computer can understand. 
- The programmer needs to have skills in symbolic programming in such AI languages as LISP, Prolog and OPS5 and also some experience in the application of different types of expert system shells. 
- In addition, the programmer should know conventional programming languages like C, Pascal, FORTRAN and Basic.

<mark style="background: #69E7E4;">Project Manager:</mark>
- The <mark style="background: #69E7E4;">project manager</mark> is the leader of the expert system development team, responsible for keeping the project on track. 
- He or she makes sure that all deliverables and milestones are met, interacts with the expert, knowledge engineer, programmer and end-user.

<mark style="background: #69E7E4;">End user:</mark>
- The end-user, often called just the <mark style="background: #69E7E4;">user</mark>, is a person who uses the expert system when it is developed. The user must not only be confident in the expert system performance but also feel comfortable using it. 
- Therefore, the design of the user interface of the expert system is also vital for the project’s success; the end-user’s contribution here can be crucial.

### <mark style="background: #69E7E4;">Structure of a rule-based expert system:</mark>

In the early seventies, Newell and Simon from
Carnegie-Mellon University proposed a production system model, the foundation of the modern rule-based expert systems.

The production model is based on the idea that humans solve problems by applying their knowledge (expressed as production rules) to a given problem represented by problem-specific information.

The production rules are stored in the long-term memory and the problem-specific information or facts in the short-term memory.

### <mark style="background: #69E7E4;">Production system model:</mark>

![](https://i.imgur.com/ug2yCrq.png)

### <mark style="background: #69E7E4;">Basic structure of a rule-based expert system:</mark>

![](https://i.imgur.com/aZpCi9V.png)

The <mark style="background: #69E7E4;">knowledge base</mark> contains the domain knowledge useful for problem solving. In a rule-based expert system, the knowledge is represented as a set of rules. Each rule specifies a relation, recommendation, directive, strategy or heuristic and has the IF (condition) THEN (action) structure.

When the condition part of a rule is satisfied, the rule is said to <mark style="background: #69E7E4;">fire</mark> and the action part is executed.

The <mark style="background: #69E7E4;">database</mark> includes a set of facts used to match against the IF (condition) parts of rules stored in the knowledge base.

The <mark style="background: #69E7E4;">inference engine</mark> carries out the reasoning whereby the expert system reaches a solution. It links the rules given in the knowledge base with the facts provided in the database.

The <mark style="background: #69E7E4;">explanation facilities</mark> enable the user to ask the expert system <mark style="background: #69E7E4;">how</mark> a particular conclusion is reached and <mark style="background: #69E7E4;">why</mark> a specific fact is needed. An expert system must be able to explain its reasoning and justify its advice, analysis or conclusion.

The <mark style="background: #69E7E4;">user interface</mark> is the means of communication between a user seeking a solution to the problem and an expert system.

### <mark style="background: #69E7E4;">Complete structure of a rule-based expert system:</mark>

![](https://i.imgur.com/NgQvjPQ.png)

### <mark style="background: #69E7E4;">Characteristics of an expert system:</mark>

An expert system is built to perform at a human expert level in a <mark style="background: #69E7E4;">narrow, specialised domain</mark>.

Thus, the most important characteristic of an expert system is its high-quality performance. No matter how fast the system can solve a problem, the user will not be satisfied if the result is wrong.

On the other hand, the speed of reaching a solution is very important. Even the most accurate decision or diagnosis may not be useful if it is too late to apply, for instance, in an emergency, when a patient dies or a nuclear power plant explodes.

Expert systems apply <mark style="background: #69E7E4;">heuristics</mark> to guide the reasoning and thus reduce the search area for a solution.

A unique feature of an expert system is its <mark style="background: #69E7E4;">explanation capability</mark>. It enables the expert system to review its own reasoning and explain its decisions.

Expert systems employ <mark style="background: #69E7E4;">symbolic reasoning</mark> when solving a problem. Symbols are used to represent different types of knowledge such as facts, concepts and rules.

### <mark style="background: #69E7E4;">Can expert systems make mistakes?</mark>

Even a brilliant expert is only a human and thus can make mistakes. 

This suggests that an expert system built to perform at a human expert level also should be allowed to make mistakes. 

We still trust experts, even though  we recognise that their judgements are sometimes wrong. 

Likewise, at least in most cases, we can rely on solutions provided by expert systems, but mistakes are possible and we should be aware of this.

In expert systems, <mark style="background: #69E7E4;">knowledge is separated from its processing</mark> (the knowledge base and the inference engine are split up). A conventional program is a mixture of knowledge and the control structure to process this knowledge. This mixing leads to difficulties in understanding and reviewing the program code, as any change to the code affects both the knowledge and its processing.

When an expert system shell is used, a knowledge engineer or an expert simply enters rules in the knowledge base. Each new rule adds some new knowledge and makes the expert system smarter.

### <mark style="background: #69E7E4;">Comparison of expert systems with conventional systems and human experts</mark>

![](https://i.imgur.com/DboaurR.png)
![](https://i.imgur.com/jHVICEl.png)

### <mark style="background: #69E7E4;">Forward chaining and backward chaining:</mark>

In a rule-based expert system, the domain knowledge is represented by a set of IF-THEN production rules and data is represented by a set of facts about the current situation. The inference engine compares each rule stored in the knowledge base with facts contained in the database. When the IF (condition) part of the rule matches a fact, the rule is <mark style="background: #69E7E4;">fired</mark> and its THEN (action) part is executed.

The matching of the rule IF parts to the facts produces <mark style="background: #69E7E4;">inference chains</mark>. The inference chain indicates how an expert system applies the rules to reach a conclusion.

### <mark style="background: #69E7E4;">Inference engine cycles via a match-fire procedure:</mark>

![](https://i.imgur.com/EHkEynj.png)

![](https://i.imgur.com/LKzSFDw.png)

### <mark style="background: #69E7E4;">Forward Chaining:</mark>

Forward chaining is the <mark style="background: #69E7E4;">data-driven reasoning</mark>. 

The reasoning starts from the known data and proceeds forward with that data. 

Each time only the topmost rule is executed. When fired, the rule adds a new fact in the database. Any rule can be executed only once. 

The match-fire cycle stops when no further rules can be fired.

![](https://i.imgur.com/Pgfaaox.png)

Forward chaining is a technique for gathering information and then inferring from it whatever can be inferred.

However, in forward chaining, many rules may be executed that have nothing to do with the established goal.

Therefore, if our goal is to infer only one particular fact, the forward chaining inference technique would not be efficient.

### <mark style="background: #69E7E4;">Backward chaining:</mark>

Backward chaining is the <mark style="background: #69E7E4;">goal-driven reasoning</mark>. In backward chaining, an expert system has the goal (a <mark style="background: #69E7E4;">hypothetical solution</mark>) and the inference engine attempts to find the evidence to prove it. 

First, the knowledge base is searched to find rules that might have the desired solution. Such rules must have the goal in their THEN (action) parts. 

If such a rule is found and its IF (condition) part matches data in the database, then the rule is fired and the goal is proved. However, this is rarely the case.

Thus the inference engine puts aside the rule it is working with (the rule is said to <mark style="background: #69E7E4;">stack</mark>) and sets up a new goal, a subgoal, to prove the IF part of this rule. 

Then the knowledge base is searched again for rules that can prove the subgoal. The inference engine repeats the process of stacking the rules until no rules are found in the knowledge base to prove the current subgoal.

![](https://i.imgur.com/wRb0vPl.png)

### <mark style="background: #69E7E4;">How do we choose between forward and backward chaining?</mark>

If an expert first needs to gather some information and then tries to infer from it whatever can be inferred, choose the forward chaining inference engine.

However, if your expert begins with a hypothetical solution and then attempts to find facts to prove it, choose the backward chaining inference engine.

### <mark style="background: #69E7E4;">Conflict resolution:</mark>

Earlier we considered two simple rules for crossing a road. Let us now add third rule:

![](https://i.imgur.com/PMETmAS.png)

We have two rules, Rule 2 and Rule 3, with the same IF part. Thus both of them can be set to fire when the condition part is satisfied. These rules represent a conflict set. The inference engine must determine which rule to fire from such a set. A method for choosing a rule to fire when more than one rule can be fired in a given cycle is called <mark style="background: #69E7E4;">conflict resolution</mark>.

In forward chaining, <mark style="background: #69E7E4;">BOTH</mark> rules would be fired. <mark style="background: #69E7E4;">Rule 2</mark> is fired first as the topmost one, and as a result, its THEN part is executed and linguistic object <mark style="background: #69E7E4;">action</mark> obtains value <mark style="background: #69E7E4;">stop</mark>. However, <mark style="background: #69E7E4;">Rule 3</mark> is also fired because the condition part of this rule matches the fact ‘traffic light’ is <mark style="background: #69E7E4;">red</mark>, which is still in the database. As a consequence, object <mark style="background: #69E7E4;">action</mark> takes new value <mark style="background: #69E7E4;">go</mark>.

### <mark style="background: #69E7E4;">Methods used for conflict resolution:</mark>

Fire the rule with the <mark style="background: #69E7E4;">highest priority</mark>. In simple applications, the priority can be established by placing the rules in an appropriate order in the knowledge base. Usually this strategy works well for expert systems with around 100 rules.

Fire the <mark style="background: #69E7E4;">most specific rule</mark>. This method is also known as the <mark style="background: #69E7E4;">longest matching strategy</mark>. It is based on the assumption that a specific rule processes more information than a general one.

Fire the rule that uses the <mark style="background: #69E7E4;">data most recently entered</mark> in the database. This method relies on time tags attached to each fact in the database. In the conflict set, the expert system first fires the rule whose antecedent uses the data most recently added to the database.

### <mark style="background: #69E7E4;">Metaknowledge:</mark>

Metaknowledge can be simply defined as <mark style="background: #69E7E4;">knowledge about knowledge</mark>. Metaknowledge is knowledge about the use and control of domain knowledge in an expert system.

In rule-based expert systems, metaknowledge is represented by <mark style="background: #69E7E4;">metarules</mark>. A metarule determines a strategy for the use of task-specific rules in the expert system.

### <mark style="background: #69E7E4;">Metarules:</mark>

<mark style="background: #69E7E4;">Metarule 1:</mark> Rules supplied by experts have higher priorities than rules supplied by novices.

<mark style="background: #69E7E4;">Metarule 2:</mark> Rules governing the rescue of human lives have higher priorities than rules concerned with clearing overloads on power system equipment.

### <mark style="background: #69E7E4;">Advantages of rule-based expert systems:</mark>

<mark style="background: #69E7E4;">Natural knowledge representation.</mark> An expert usually explains the problem-solving procedure with such expressions as this: “In such-and-such situation, I do so-and-so”. These expressions can be represented quite naturally as IF-THEN production rules.

<mark style="background: #69E7E4;">Uniform structure.</mark> Production rules have the uniform IF-THEN structure. Each rule is an independent piece of knowledge. The very syntax of production rules enables them to be self-documented.

<mark style="background: #69E7E4;">Separation of knowledge from its processing.</mark> The structure of a rule-based expert system provides an effective separation of the knowledge base from the inference engine. This makes it possible to develop different applications using the same expert system shell.

<mark style="background: #69E7E4;">Dealing with incomplete and uncertain knowledge.</mark> Most rule-based expert systems are capable of representing and reasoning with incomplete and uncertain knowledge.

### <mark style="background: #69E7E4;">Disadvantages of rule-based expert systems:</mark>

<mark style="background: #69E7E4;">Opaque relations between rules</mark>. Although the individual production rules are relatively simple and self-documented, their logical interactions within the large set of rules may be opaque. Rule-based systems make it difficult to observe how individual rules serve the overall strategy.

<mark style="background: #69E7E4;">Ineffective search strategy</mark>. The inference engine applies an exhaustive search through all the production rules during each cycle. Expert systems with a large set of rules (over 100 rules) can be slow, and thus large rule-based systems can be unsuitable for real-time applications.

<mark style="background: #69E7E4;">Inability to learn</mark>. In general, rule-based expert systems do not have an ability to learn from the experience. Unlike a human expert, who knows when to “break the rules”, an expert system cannot automatically modify its knowledge base, or adjust existing rules or add new ones. The knowledge engineer is still responsible for revising and maintaining the system.