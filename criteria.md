# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
I expect the dining hall question to be the hardest. The dining documents are spread across several posts — the Pellew chunk is a reply that adds to earlier posts — and each one covers many things at once, so the answer may not sit in a single chunk. That's why 4 of 5 rather than 5 of 5.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
When I ran questions in Milestone 1, every answer printed a Sources line, 5 out of 5 — even the weak parking answer. The only time no source appeared was when the gate refused the question. This is either working or it isn't, so there's no reason to accept less than 5 of 5.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

**Why this target:**
In Milestone 1, "where is the helping center" scored 0.737 and was refused, but "what to do on Saturday" scored 0.597 and got through just under the 0.6 cutoff. So I expect most out-of-scope questions to be refused, but one might sneak through close to the line the same way. That's why 4 of 5 and not 5 of 5. I'll revisit this after setting the cutoff in Milestone 4.


---

## 4. Something about your chunks

At least 4 of 5 sampled chunks cover no more than 3 topics. 
A new topic starts when the chunk changes subject — e.g. from the building's bathrooms to its laundry costs.

**Why this target:**
I ran  python app.py chunks -n 5 on campus_life and counted topics on each chunk and found 2,2,1,3,5. The 5-topic chunk(Innisfree Hall) mixed building history,bathrooms, air conditioning, laundry cost, and noise bothered me because a question about laundry would pull in four unrealted things. I chose 3 because it's the smallest limit that lets the four normal chunks pass while catching the Innisfree Hall chunk.

---

## 5. Your choice

For at least 4 of my 5 test questions, at least 4 of the 5 retrieved sources are about the question's topic.
A source counts as "about the topic" if the document mentions the thing the question asks about — for example, a parking question should return documents that mention parking.

**Why this target:**
When I asked about parking permits, the system retrieved 5 sources, but only 1 was about parking. The other 4 were about graduation, dining, advising and the shuttle — nothing to do with the question. That bothered me more than the answer itself: four unnecessary sources is mostly noise. I will only call retrieval "working" when at least 4 of the 5 sources are actually about what was asked.


---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
