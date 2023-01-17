name: CI
on:
push:
branches:
- main
  pull_request:
  types: [opened, synchronize]

jobs:
build:
runs-on: ubuntu-latest
steps:
- name: Checkout
  uses: actions/checkout@v2
- name: Set up JDK
  uses: actions/setup-java@v1
  with:
  java-version: 1.8
- name: Build with Gradle
  run: ./gradlew clean test
- name: Import results to Xray
  env:
  JIRA_USERNAME: ${{ secrets.JIRA_USERNAME }}
  JIRA_API_TOKEN: ${{ secrets.JIRA_API_TOKEN }}
  JIRA_SERVER: ${{ secrets.JIRA_SERVER }}
  TEST_RESULTS_PATH: ${{ env.TEST_RESULTS_PATH }}
  run: java -jar xray-connector.jar -jira.username=$JIRA_USERNAME -jira.password=$JIRA_API_TOKEN -jira


# https://github.com/marketplace/actions/xray-action
- uses: deblockt/cucumber-report-annotations-action@v1.7
  with:
  access-token: ${{ secrets.GITHUB_TOKEN }}
  path: "**/cucumber-report.json"

- name: "Import results to Xray"
  uses: mikepenz/xray-action@{latest-release}
  with:
  username: ${{ secrets.XRAY_CLIENT_ID }}
  password: ${{ secrets.XRAY_CLIENT_SECRET }}
  testFormat: "junit"
  testPaths: "**/test/*.xml"
  testExecKey: "TEST-1"
  projectKey: "TEST"