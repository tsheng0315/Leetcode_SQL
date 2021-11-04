## Top Competitors

https://www.hackerrank.com/challenges/full-score/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

Use `Hackers`, `Difficulty`,`Challenges`, `Submissions` tables to assembling the leaderboard.

* print `hacker_id` and `name` of hackers who achieved full scores for more than one challenge. 

* Order output in descending order by the total number of challenges in which the hacker earned a full score. 

* same number of challenges, sort hackers by ascending `hacker_id`.

### my code
#### failed
```mysql
select hackers.hacker_id, hackers.name
from Hackers, Submissions, Challenges, difficulty
where Submissions.score in (select Difficulty.score from difficulty) 
group by hackers.hacker_id
having count(submission._id)>1
```

#### other's
```mysql
select h.hacker_id,h.name from hackers h,challenges c ,difficulty d,submissions s 
where h.hacker_id=s.hacker_id
and c.challenge_id=s.challenge_id
and c.difficulty_level=d.difficulty_level
and s.score=d.score
group by h.hacker_id,h.name having  count(h.hacker_id)>1
 order by count(c.challenge_id) desc,h.hacker_id
 ```
