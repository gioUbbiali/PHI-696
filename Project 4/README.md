**The SPARQL Library of Buffalo**

[Codewars](https://www.codewars.com/dashboard) is a website designed to facilitate algorithmic training for various programming languages. Users supply problem statements and others provide coding solutions to those problems. For example, you might find a problem for Python such as: 

```
Define a function that returns the length of a given string. 
```

With a solution like: 

```
def length_of_string(s):
	return len(s)
```
	
Codewars is not limited to traditional programming languages like Python, but also facilitates training for languages like SQL. As you have learned, SQL and SPARQL are both query languages, but what might surprise you is that there is currently no option for training SPARQL in Codewars. This project will go some way to remedy that. 

For this project, you will be tasked with constructing SPARQL problems for the codewars site. 

```
Note #1: Completion of this task will not require you to actually have your SPARQL problems successfully posted to codewars. Adding problems to codewars takes more time than we have for this project. Additionally, you are only allowed to add propose problems to codewars if you have a certain amount of experience (specifically, you need 300 of what they call 'honor points', which is acquired by solving problems). At some point, assuming you permit it, I will post your problems to codewars (giving you credit of course). 
Note #2: The potential for this project to directly impact the ontology community is clear. SPARQL can be challenging, and there are few opportunities for drill practice like this. 
Note #3: You will not be required to learn a programming language, though you will likely need to expand your comfort with computer science jargon; if you hit a wall, ask your peers for help; if the wall persists, ask me. 
Note #4: Codewars provides a guidebook - https://docs.codewars.com/authoring/tutorials/create-first-kata/ - for creating problems; I strongly encourage you to read it, since the standard provided there is how I will be evaluating success. 
```
**Assignment Details**

Problems on Codewars are ranked in terms of difficulty. The lowest "kata" - 8 - indicates a rather easy problem, while the highest kata - 1 - indicates a very challenging problem. 

For our purposes, harder kata will be worth more points than easier kata, and you are required to submit enough kata to acquire 100 points according to the following point system: 

  |   **kata**    |  **points**   |
  | ------------- | ------------- |
  |       1       |      35       |
  |       2       |      25       |
  |       3       |      20       |
  |       4       |      10       |
  |       5       |       5       |
  |       6       |       3       |
  |       7       |       2       |
  |       8       |       0       |

You're probably thinking, "why would I submit a level 8 kata if they're not worth any points?" Great question. Because everyone had to submit at least one level 8 kata. Otherwise, you're permitted to submit kata in any distribution you choose. For example, you might submit 2 problems for kata one (70 points), one for kata 3 (20 points), one for kata 4 (10 points), and one for kata 8 (0 points but required). 

It is your responsibility and the responsibility of your peers reviewing your submission in PR to determine whether your submission is ranked appropriately. In the event that consensus is reached that your kata is ranked inappropriately, you must work with your peers to revise the submission so that it is either more or less challenging, accordingly. You are not permitted to submit new problems with different strengths after PRs are open, but must instead revise your PRs. So, think hard about how challenging your submission is. 

There is one other option for those desiring a different sort of challenge. If you provide alongside your SPARQL submission a translation of the same problem into SQL, complete with documentations, solution, etc. then you may receive half points extra at that kata level (rounded up). For example, if you submit a SPARQL problem that is kata rank 1 and also submit a SQL version of that same problem, you  will receive 35+18=53 points. 


Here are our schemas:

Prefix schema:
rdf:
rdfs:

Animal schema:
ex:animal a rdfs:Class .
ex:eats a rdf:Property ; 
                       rdfs:domain ex:animal ; 
                       rdfs:range ex:food . 
Food schema:
ex:food a rdfs:Class .
ex:eaten by a rdf:Property ; 
                       rdfs:domain ex:food ; 
                       rdfs:range ex:animal . 

ex:has_name a rdf:Property ; 
                      rdfs:domain owl:thing ;
                      rdfs:range xsd:string .

ex:rabbit 1 a ex:animal;
                     ex.has_name 'rabbit 1'.

Exercise 1:
Taka question: Select names of food that all animals eat.

Solution: we wrote the following SPARQL Query.

PREFIX ex: http://example.org/animals/  

SELECT ?name?food
 WHERE
   {
  	?animals ex:eats ?food ;
        ?food ex:has_name ?name .
   }

We should get all names of all foods eaten by any animal.


Exercise 2:
Taka question: Select Select names of food eaten by cats.

Solution: we wrote the following SPARQL Query.

PREFIX ex: http://example.org/animals/  
SELECT ?name?food
 WHERE
   {
        ?animal ex:eats ?food ;
        ?animal ex:has_name ?cat ;

 You cannot do this because your has_name property only links with food, as declared in the schema
 
        ?food rdfs:has_name ?name .
   }

We should get all names of foods eaten by cats.


Exercise 3:
Taka question: Select names of animals eating carrots.

Solution: we wrote the following SPARQL Query.

PREFIX rdfs: http://example.org/food/  
SELECT ?name?animal

You are not declaring any ?name variable in the rest of the query. The computer won't know what you refer to by ?name

 WHERE
   {
       
	ex:animal ex: has_name ?name ;
	?food ex:eaten by ?animal ;
        ?food ex:has_name "carrot" .

    }

We should get all names of animals that eat carrots.
