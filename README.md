# Jenkins for Symfony 2
## What?

This is just a simple ant build.xml file which will help you get your Symfony2 project in Jenkins.

It's a Symfony2-specific amalgamation of [Jenkins PHP](http://jenkins-php.org/)'s build file (and for it to work properly, I strongly suggest you follow their setup guidelines) and some bits and bobs I've found all over the intertubez and can't attribute to anyone in particular. It's clever enough to ignore your SF2 cache folders. It will automagically test all your bundles. If you want a different job per bundle, you'll have to do some tweaking of your own.
 
It has two build targets: build, and build-full. The default *build* will just run your unit tests. The other, *build-full*, will run all unit tests, PHP syntax checker, the PHP Mess Detector and PHP LOC. The *build-full* target can take quite a while, so I only run that once a day, while the *build* target is executed after every commit.

I've also included a PHPMD config file. If you don't want to use PHPMD you can just ignore it. If you want to write your own, just plonk it in the build folder and it'll Just Workt(tm).

## Requirements

1. Jenkins
2. A Symfony2 project :-)
3. Apache Ant 
4. PHPMD [Ant Task](http://phpmd.org/documentation/ant-task.html)
5. PHPUnit 3.6+

## Setup

	cd YOUR_SYMFONY2_PROJECT
	mkdir build
	cd build
	wget https://raw.github.com/Nimlhug/Jenkins4Symfony2/master/build.xml
	wget https://raw.github.com/Nimlhug/Jenkins4Symfony2/master/phpmd.xml

Commit your changes to your project, and then move on to the Jenkins Setup.

## Jenkins Setup

Hopefully you already know how to add a project to Jenkins. If you don't, check out [the Jenkins Documentation](https://wiki.jenkins-ci.org/display/JENKINS/Building+a+software+project). Once you've done that, come take a look at this screenshot. Just make sure Jenkins can access your complete SF2 project tree. 

![Jenkins Setup](https://raw.github.com/Nimlhug/Jenkins4Symfony2/master/jenkins.png)

If you want all the PHPMD goodness and PHP LOC graphs, simply add another jenkins job and change the Ant target to *build-full*.

That's all! Jenkins should now happily build your project. Drop me a line if you have any questions.
