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
    '$stop = ea.sc.cumulativeFidelity(v = 3000)' \
    '$name = "sr-tree-cf-03k"' \
    '$seeds = [1:1:30]'
```

Stop criterion: cumulative fidelity > 10k 
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree.txt \
  --expHeadLines \
    '$stop = ea.sc.cumulativeFidelity(v = 10000)' \
    '$name = "sr-tree-cf-10k"' \
    '$seeds = [1:1:30]'
```

Stop criterion: elapsed time > 3 
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree.txt \
  --expHeadLines \
    '$stop = ea.sc.elapsed(v = 3)' \
    '$name = "sr-tree-t-03"' \
    '$seeds = [1:1:30]'
```

Stop criterion: elapsed time > 10
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree.txt \
  --expHeadLines \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$name = "sr-tree-t-10"' \
    '$seeds = [1:1:30]'
```
