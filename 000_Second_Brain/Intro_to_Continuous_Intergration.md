11/11/2024 0724

Status #idea

Tags:

# Intro to Continuous Intergration

The core idea is very simple
	Frequent code integrations
	Automated Builds and tests
	Early bug detection - will improve quality
	Faster Dev Cycle
*Key concepts*
Frequent Integrations - this encourages developers to upload code to repositories several times a day.
Automation - ensures consistency and accuracy
Version control - important to allow developers to work on the same code base at the same time.
*Benefits*
Early bug detection - by running tests, bug will be caught early and at these early points its easier to fix and cheaper.
Faster Deployment
Improved Collaboration
Reduced Cost - building faster and better quality

*Automated Testing*

This is at the heart of CI, it gives us the confidence that our code changes haven't broken the current app state.
Unit tests - test functions, fast and numerous test individual components.
Integration Tests - Check how different parts work together
E2E (End 2 End) - Simulate real user scenarios, comprehensive typically toward the end of production
Automated testing is about catching as many issues as possible, getting them all is virtually impossible.

*Popular CI Tools*

Jenkins - Oldest and widely used open source automation server with extensive plugin ecosystem. Highly customisation and widely used in enterprise environments.

Gitlab CI - This is built into gitlab, integrated CI/CD solution within gitlab. Offers integration with gitlab repositories and built in docker support

GitHub Actions - very similar to gitlab, github's native CI/CD solutions tightly integrated with github repositories, offering workflow automation and east set up.

Each of these has its own strengths and will often be decided on the current infrastructure and specific needs.

*CI pipeline architecture*

Source control - Build Automation - Testing - Report

The CI pipeline automatically moves code changes through the stages of building, testing and reporting, ensuring code quality integration at every step
Next step will be CD pipeline.

**Continuous Deliver and deployment**

Zero human intervention
Automating the path from code to production.

*Key concepts*
	Automation of release process deployment pipline
	Production like environments
	Monitoring and feedback
*Benefits*
	Faster time to market
	lower risk releases
Improved developer productivity
Higher customer satisfaction






# References
