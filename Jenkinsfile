#!groovy

library "knime-pipeline@master"

properties([
    buildDiscarder(logRotator(numToKeepStr: '5')),
    disableConcurrentBuilds(),
    parameters([booleanParam(defaultValue: false, description: 'Whether this is a release build', name: 'RELEASE_BUILD')])
])

try {
    knimetools.defaultMavenBuild(nodeLabel: 'maven && java17')
} catch (ex) {
    currentBuild.result = 'FAILED'
    throw ex
} finally {
    notifications.notifyBuild(currentBuild.result);
}
/* vim: set shiftwidth=4 expandtab smarttab: */

