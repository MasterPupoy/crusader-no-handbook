## Non UI

### Strive for solutions that makes impossible state impossible to represent
tools to do so includes [single-source-of-truth](#single-source-of-truth), [expose features](#expose-features-not-implem-details), etc
### expose features, not implem details
a good example is when dealing with statuses, 
```
# bad
POST /status/:id
{ "status": "block" }

# good
POST /block/:id
```
Big reason behind this is that we don't want to ask consumers to do program updates unless features were really changed, implementation detail changes should not require movement from consumers
### Single source of truth
this rule is best fitted for transactional data, not so much for reporting due to redundancies/perf reasons etc, but still a good default rule to follow
