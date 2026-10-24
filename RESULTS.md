# K6 lab results 
  
## Part 0 
- Step 0.1, http_req_duration: 307.42ms
- Step 0.2, requests, rate and p(95), and why the rate stays below 5:
    - requests = 75
    - rate = 3.549921/s requests per second 
    - p(95) = 401.19
    - rate stay below 5 because it have sleep(1) like after VU sent req they have to with 1 s,so the total rate for 5 VUs will not more than 5.
- Step 0.6, exit code of the normal run and of the run with P95=300: 
    - the normal run: all requests are completed, and thresholds are checked, and no interrupted no error. exit code is 0
    - run with P95=300: all requests are completed, but have the error on http_req_duratio threshold because p(95) is > 300. exit code is 99
- Step 0.7, rules that passed, p(95), p(99), exit code after your change: 
    - rules that pass = 'rate>0.99', 'p(95)<1000', 'p(99)<1500', 'rate<0.01'
    - p(95) = 598.21ms
    - p(99) = 742.96ms
    - exit code after change (edit P95=400) = 99
- Step 0.8, what was wrong, and how the checks showed it: 
  
## Part A results 
| Step | Test type    | Users | Req/s | p(95) | Max | Failed | Checks | 
| ---- | ------------ | ----- | ----- | ----- | --- | ------ | ------ | 
| A1   | Smoke        | 1     |       |       |     |        |        | 
| A2   | Average load | 3     |       |       |     |        |        | 
| A3   | Stress       | 5     |       |       |     |        |        | 
| A4   | Spike        | 5     |       |       |     |        |        | 
| A5   | Soak         | 2     |       |       |     |        |        | 
  
## Part B 
1. Fill in the results table for Steps A1 to A5. 

2. In Step 0.2, why was the request rate below 5 requests per second with 5 virtual users? 

3. Did the response time grow from the average-load test to the stress test? Explain your answer with the operational envelope. 

4. In the spike test, how long did the response time take to return to normal after the spike? 

5. In the soak test, did the response time or the error rate get worse over time? Name one kind of defect that a soak test of several hours could reveal. 

6. Why do the thresholds in this lab use p(95) rather than the average?

7. Your results come from a shared public site reached over the internet. Give two reasons why the same tests against a system in a lab could give different numbers. 

8. Why must you never run a stress, spike or breakpoint test with hundreds of users against a site that you do not own? 

9. Write one vague performance requirement for an app you use every day. Rewrite it as a testable requirement, and show the K6 thresholds that check it. 