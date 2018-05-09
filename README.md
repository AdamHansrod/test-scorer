# Test Scorer

[![Build Status](https://travis-ci.org/SteveSmithCD/test-scorer.svg?branch=master)](https://travis-ci.org/SteveSmithCD/test-scorer) [ ![Download](https://api.bintray.com/packages/SteveSmithCD/releases/test-scorer/images/download.svg) ](https://bintray.com/SteveSmithCD/releases/test-scorer/_latestVersion)

A lightweight, portable way to distinguish between deterministic success, deterministic failure, and non-deterministic 
failure when running automated tests. 

## What is Test Scorer?

`test-scorer` helps you to identify which of your unit tests and/or acceptance tests are consistently failing, and 
which are inconsistently failing. Non-deterministic automated tests have an insidious impact on teams, best described
by Martin Fowler in [Eradicating Non-Determinism in Tests](https://www.martinfowler.com/articles/nonDeterminism.html). 
While some open-source build servers have test report plugins that show at a glance which particular tests have been
failing for the past *n* builds, there is rarely a test-centric perspective available that ranks the deterministic
and non-deterministic failures worthy of your precious time.

## How does Test Scorer work?

The idea is for `test-scorer` to work with data supplied by your build server - in any build server, in fact. If your
build server has enough historical data in its build artifacts, a build job can be setup on a regular schedule to 
download the latest *n* test reports for a test suite of your choice and invoke `test-scorer` as you wish. 
Alternatively, a post-build hook could be added to the build server in order to push the latest test report to a 
closed-source microservice reliant on`test-scorer` for test scores. 

[Dave Hounslow](https://www,twitter.com/thinkfoo) pithily decribed the algorithm used as *"Last n builds, each test 
scores 1 for a failure, multiply by n for most recent build through 1  for oldest. Sum this. Sort descending"*  

Users of `test-scorer` are encouraged to write their own test report parsers and scored tests formatters, as they wish.

## Where do I get Test Scorer?

At the moment, Test Scorer is run from source only. Later on, it will be built on an open build server and published 
to Bintray or similar.

## How do I build Test Scorer?

To build `test-scorer` locally, clone the repository and run `./gradlew clean test` on the command line. That will 
compile the code, run the tests, and create a release candidate.

## Where did Test Scorer come from?

`test-scorer` is inspired by the closed-source AutoTrish tool built by [LMAX](www.lmax.com) c2009, which was an 
attempt to automate the hard work of [Trisha Gee](https://github.com/trishagee) on intermittent acceptance tests. 
[Dave Farley](https://www.twitter.com/DaveFarley77) has described it in several public talks on Continuous Delivery at LMAX, including "The process, 
technology and practice of Continuous Delivery" at [QCon London 2014](https://qconlondon.com/london-2014/london-2014/speaker/Dave+Farley.html).  
 
Thanks to Dave Farley and Dave Hounslow for the shared memory recall, and encouragement. :)  