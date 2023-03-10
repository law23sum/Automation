Cucumber-Junit : "io.cucumber:cucumber-junit:$cucumberJvmVersion"
Cucumber-xray : "com.smartbear.cucumber:cucumber-xray:$cucumberXrayVersion"
Cucumber-xray-connector : "com.smartbear.cucumber:cucumber-xray-connector:$cucumberXrayVersion"
Junit : "junit:junit:4.13"
Logging : "org.slf4j:slf4j-api:1.7.30"
Selenium-support : "org.seleniumhq.selenium:selenium-support:$seleniumVersion"
Testcontainers : "org.testcontainers:testcontainers:1.14.3"
Testcontainers-cucumber : "org.testcontainers:testcontainers-cucumber:1.14.3"








///*
// * This file was generated by the Gradle 'init' task.
// *
// * This is a general purpose Gradle build.
// * Learn more about Gradle by exploring our samples at https://docs.gradle.org/7.6/samples
// */
//https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions
//
//plugins {
//    id 'cucumber-jvm'
//}
//
//// Configure Gradle Wrapper
//wrapper {
//    gradleVersion = '6.7'
//}
//
//version = '1.2'
//tasks.named('compileJava') {
//    // use the project's version or define one directly
//    options.javaModuleVersion = provider { project.version }
//}
//
//// Define project properties
//ext {
//    seleniumVersion = '3.141.59'
//    webdrivermanagerVersion = '3.11.0'
//    cucumberXrayVersion = '5.5.0'
//    cucumberJvmVersion = '6.10.3'
//    javaVersion = '1.8'
//}
//
//// Configure dependencies
//dependencies {
//    // Java
//    //   implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk$kotlin_version"
//    // Selenium
//    testImplementation "org.seleniumhq.selenium:selenium-java:$seleniumVersion"
//    // Webdrivermanager
//    testImplementation "io.github.bonigarcia:webdrivermanager:$webdrivermanagerVersion"
//    // Cucumber-JVM
//    testImplementation "io.cucumber:cucumber-java:$cucumberJvmVersion"
//    testImplementation "io.cucumber:cucumber-junit:$cucumberJvmVersion"
//    //Cucumber-Xray
//    testImplementation "com.smartbear.cucumber:cucumber-xray:$cucumberXrayVersion"
//    // Other dependencies
//    testImplementation 'junit:junit:4.13'
//    testImplementation 'org.slf4j:slf4j-api:1.7.30'
//    testImplementation 'org.seleniumhq.selenium:selenium-support:$seleniumVersion'
//    testImplementation 'org.testcontainers:testcontainers:1.14.3'
//    testImplementation 'org.testcontainers:testcontainers-cucumber:1.14.3'
//
//}
//
//dependencies {
//    testImplementation 'io.cucumber:cucumber-java:x.y.z'
//    testImplementation 'io.cucumber:cucumber-junit:x.y.z'
//}
//tasks.test {
//    useJUnitPlatform()
//    systemProperty("cucumber.junit-platform.naming-strategy", "long")
//}
//
//
//tasks {
//
//    val consoleLauncherTest by registering(JavaExec::class) {
//        dependsOn(testClasses)
//        val reportsDir = file("$buildDir/test-results")
//        outputs.dir(reportsDir)
//        classpath = sourceSets["test"].runtimeClasspath
//        main = "org.junit.platform.console.ConsoleLauncher"
//        args("--scan-classpath")
//        args("--include-engine", "cucumber")
//        args("--reports-dir", reportsDir)
//    }
//
//    test {
//        dependsOn(consoleLauncherTest)
//        exclude("**/*")
//    }
//}




//defaultTasks 'clean', 'test', 'aggregate'
//
//wrapper {
//    gradleVersion = '7.6'
//}
//
//repositories {
//    mavenLocal()
//    jcenter()
//}
//
//buildscript {
//    repositories {
//        mavenLocal()
//        jcenter()
//    }
//    dependencies {
//        classpath("net.serenity-bdd:serenity-gradle-plugin:2.4.24")
//        classpath("net.serenity-bdd:serenity-single-page-report:2.4.24")
//    }
//}
//
//apply plugin: 'java'
//apply plugin: 'eclipse'
//apply plugin: 'idea'
//apply plugin: 'net.serenity-bdd.aggregator'
//
//sourceCompatibility = 11
//targetCompatibility = 11
//
//serenity {
//    reports = ["single-page-html"]
//}
//
//dependencies {
//    testImplementation 'net.serenity-bdd:serenity-core:2.6.0'
//    testImplementation 'net.serenity-bdd:serenity-cucumber6:2.6.0'
//    testImplementation 'net.serenity-bdd:serenity-screenplay:2.6.0'
//    testImplementation 'net.serenity-bdd:serenity-screenplay-webdriver:2.6.0'
//    testImplementation 'net.serenity-bdd:serenity-rest-assured:2.6.0'
//    testImplementation 'io.rest-assured:rest-assured:4.3.2'
//    testImplementation(platform('org.junit:junit-bom:5.9.2'))
//    testImplementation('org.junit.jupiter:junit-jupiter')
//}
//
//test {
//    useJUnitPlatform()
//    testLogging {
//        events "passed", "skipped", "failed"
//    }
//    testLogging.showStandardStreams = true
//    systemProperties System.getProperties()
//}
//
//gradle.startParameter.continueOnFailure = true
//
//test.finalizedBy(aggregate)