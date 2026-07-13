# Decision Log — <your name>, Unit 1

Copy this template into your unit's `student-work/decision-log.md`. Add one
entry per direct → interpret → extend cycle during the supervised-practice
hour. Push to your fork before asking for async help — your reasoning matters
as much as your code.

---

## Cycle 1

- **What I asked** (in my own words): betweeness and closeness highlight points in tel-aviv while highlighting king-george street.
- **What the agent did**: implemented it
- **What I understood from the result**: King george is not as central as I tought, it doesnt have any closeness highlights and barely any betweeness highlights.
- **My next question / follow-up**: I asked for a map with the same highlights and street names visisble so that I can choose a different street.

## Cycle 2

- **What I asked**: Remove eliezer kaplan street and recompute closeness and betweeness on streets.
- **What the agent did**: did that
- **What I understood from the result**: I saw the smae street appearing multiple times in the lists detailing the top 10 streets with most  closeness and betweeness
- **My next question / follow-up**: I wanted to group these streets into a single poiint. for that I asked as dual graph of the before and after removal of kaplan street.

## Cycle 3

- **What I asked**:I asked for dual graph of tel aviv with comparisons of betweeness and closeness scores before and after kaplan was removed
- **What the agent did**: did that
- **What I understood from the result**: a lot of unnamed streets appeared in the top 10 lists
- **My next question / follow-up**: I asked for the smae thing but disregard the unnamed streets since they are probably small unmeaningful alleyways or short roads.

## CYCLE 4 
- **What I asked**:I asked for visual map detailing impact of closure of kaplan street. The impact would be measured using a hybrid normalized score of the average of betweeness and closeness.
- **What the agent did**: provided a visual map as well as a bar graph displaying the top 10 delta changes (both positive and negative)
- **What I understood from the result**: The closure wouldnt have a lot of impact on main roads by this measurement (the hybrid score). It did have a major impact on 2 streets butthey arent considered main and the impact is so high I think of it as an outlier.
- **My next question / follow-up**: I decided that this was enough of an evidence that the research should stop and that the closure of kaplan street while being a main artery, will not impact the adjacent main streets as much.

---

## End-of-session rubric check

- [v] DIRECT — phrased requests using unit vocabulary, specified inputs precisely
- [v] INTERPRET — explained results in own words, noticed surprises
- [v] EXTEND — at least one follow-up grounded in a result

## One thing that surprised me today

King george wasnt a main street as I though it was. while its connected to a lot of main streets, is very central, has a lot of points of interest nearby: it didnt score high in betweeness or closeness.
