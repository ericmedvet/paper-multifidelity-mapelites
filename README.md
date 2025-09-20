# paper-multifidelity-mapelites
Software artifacts related to a novel approach for solving multi-fidelity optimization problems with a modified version of MAP-Elites

## How to reproduce the experiments

Requirements:
- JDK 21

### Tree-based regression

Stop criterion: cumulative fidelity > 3k 
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree.txt \
  --expHeadLines \
    '$name = "regression-tree-cf-03k"' \
    '$stop = ea.sc.cumulativeFidelity(v = 3000)' \
    '$seeds = [1:1:30]'
```

Stop criterion: cumulative fidelity > 10k 
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree.txt \
  --expHeadLines \
    '$name = "regression-tree-cf-10k"' \
    '$stop = ea.sc.cumulativeFidelity(v = 10000)' \
    '$seeds = [1:1:30]'
```

Stop criterion: elapsed time > 3 
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree.txt \
  --expHeadLines \
    '$name = "regression-tree-t-03"' \
    '$stop = ea.sc.elapsed(v = 3)' \
    '$seeds = [1:1:30]'
```

Stop criterion: elapsed time > 10
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree.txt \
  --expHeadLines \
    '$name = "regression-tree-t-10"' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

### Impact of the schedule
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree-schedule.txt \
  --expHeadLines \
    '$name = "regression-tree-t-10-schedule"' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

### Scalability

Assuming you are running this on a machine with at least 16 core.
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/scalability.txt \
  --expHeadLines \
    '$name = "scalability"' \
    '$time = 3' \
    '$threads = [1:1:16]' \
    '$seeds = [1:1:30]'
```
