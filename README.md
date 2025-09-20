# paper-multifidelity-mapelites
Software artifacts related to a novel approach for solving multi-fidelity optimization problems with a modified version of MAP-Elites

## How to reproduce the experiments

Requirements:
- JDK 21

### Tree-based symbolic regression

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

#### Impact of the schedule
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

#### Impact of the refresh threshold
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-tree-threshold.txt \
  --expHeadLines \
    '$name = "regression-tree-t-10-threshold"' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

#### Scalability

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

### ANN-based regression

#### Impact of descriptors

With descriptors based on number of weigths greater than a threshold:
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-ann-desc-nthreshold.txt \
  --expHeadLines \
    '$name = "regression-ann-t-10-nthredshold"' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

With descriptors based on variance of ANN weights:
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-ann-desc-variance.txt \
  --expHeadLines \
    '$name = "regression-ann-t-10-variance"' \
    '$bins = 8' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

With descriptors based on average value of genes (first and second half):
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-ann-desc-genes.txt \
  --expHeadLines \
    '$name = "regression-ann-t-10-genes"' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

#### Impact of archive size

With 12x12 archive:
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-ann-desc-variance.txt \
  --expHeadLines \
    '$name = "regression-ann-t-10-variance-12"' \
    '$bins = 12' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

With 16x16 archive:
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-ann-desc-variance.txt \
  --expHeadLines \
    '$name = "regression-ann-t-10-variance-16"' \
    '$bins = 16' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

With 20x20 archive:
```shell
java \
  -jar jgea.experimenter-2.7.1-SNAPSHOT-jar-with-dependencies.jar \
  -nt 16 -nr 1 \
  -f exp-descriptions/regression-ann-desc-variance.txt \
  --expHeadLines \
    '$name = "regression-ann-t-10-variance-20"' \
    '$bins = 20' \
    '$stop = ea.sc.elapsed(v = 10)' \
    '$seeds = [1:1:30]'
```

