# Testing binary and source builds

```
# create ns, and build-configs
oc apply -f openshift

# switch to the project
oc project s2i-test

# create an archive for the project
git archive  -o archive.tar.gz HEAD

# start various builds
oc start-build bc/binary-build --from-dir=. --follow | grep '>>>'


oc start-build bc/binary-build  \
  --from-archive=./archive.tar.gz --follow | grep '>>>'

oc start-build bc/source-build --from-dir=. --follow | grep '>>>'

oc start-build bc/source-build  \
  --from-archive=./archive.tar.gz --follow | grep '>>>'

```
