vivosys repository: git://github.com/vivosys/wordnik-oss.git
URL https://github.com/vivosys/wordnik-oss

1. Add upstream repository

    git add upstream git@github.com:wordnik/wordnik-oss

2. Switch to the proper branch

    git checkout scala_2.10.0-rc1

3. The tests that are provided require a specific Mongo server
   configuration.  Ignore the test failures due to the lack of an
   equivalent Mongo server configuration:

    REPO_ID=vivosys-repo
    REPO_URL=https://tools.vivosys.com/artifactory/ext-release-local
    mvn \
      -Dgpg.skip -Dmaven.test.failure.ignore=true \
      -DaltDeploymentRepository=$REPO_ID::default::$REPO_URL \
      source:jar javadoc:jar install deploy
