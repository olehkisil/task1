For better view please refer to README.md
at https://github.com/olehkisil/task1
-----------------------------------------



Case 1: PRODSUP-001:


Hi. I am trying to get my test cases to show up on CircleCI but it is not working. I have a fork of this project in my github account https://github.com/mtedone/podam. I added the project to CircleCI and got a green build but the Test Results tab is empty

---

Harry

=====================================================================

Case 1: PRODSUP-001:

Hi Harry,

I've checked your issue and here is my conclusion:
1) CircleCI is case-sensitive , so you need to rename your Circle.yml to  circle.yml
2) You need to enable Maven Surefire Plugin in pov.xml file in root dir
just remove below code at line 279:

<configuration>
   <skip>true</skip>
</configuration>


3) You need clear you circle.yml file and add below lines:

test:
  post:
    - mkdir -p $CIRCLE_TEST_REPORTS/junit/
    - find . -type f -regex ".*/target/surefire-reports/.*xml" -exec cp {} $CIRCLE_TEST_REPORTS/junit/ \;



More information is available here:
https://circleci.com/docs/test-metadata#metadata-collection-in-custom-test-steps

You also may check my changes at https://github.com/olehkisil/podam

BR,Oleh


========================================================================
1) setup git and circleCI
2) fork the branch
3) connect circleCI and run test
4) check results
5) read circleCI manuals
6) check if circle.yml is case sensitive
7) Circle.yml is faulty. Project runs without it.
8) looks like user's test does not reproduce any artifacts
and 
test:
 post:
   - mkdir -p $CIRCLE_TEST_REPORTS/junit/
   - find . -type f -regex ".*/target/surefire-reports/.*xml" -exec cp {} $CIRCLE_TEST_REPORTS/junit/ \;

gives no result

9)during creation of a video I've mentioned that there is a link to maven plugin that generates artifacts
10)update  pom.xml

https://github.com/olehkisil/podam
https://circleci.com/gh/olehkisil/podam/49#tests


------------------------------------------------------------------------------
Case 2: PRODSUP-002:

Hi. I added my project to CircleCI but I can’t get the build complete. I’m not sure what I’m doing wrong. Can you help? My project is https://github.com/nym2015/commons-csv.

---

Jolene


==========================================================
Hi Joline,

I'm investigating your issue and I've found something unclear for me.
Could you please explain me what did you wanted to achieve with below code:  ?

commons-csv/src/main/java/org/apache/commons/csv/CSVFormat.java  : 795
----------------------------------------------------------------
/**
* Verifies the consistency of the parameters and throws an IllegalArgumentException if necessary.
*
* @throws IllegalArgumentException
*/
private void validate() throws IllegalArgumentException {
for (int i=0; i<20*60*60; i++) {
    System.out.print('.');
    try {
        Thread.currentThread().sleep(1000);
    } catch (InterruptedException e) {
        break;
    }
}

The execution stucks on this part of code.
I've removed it just for troubleshoot and tests pass.
Please ensure that it works as expected.

Actually without change your code will also work. But test execution will take very very long time. 

RB,Oleh

==========================================================
1)fork the branch
2)run test
3)it hangs
4)check changes
5) there is some strange for 72000 + wait(1000) - try to speed up
6) looks like the method is called many times. 
7) I don't see logic in this code.
private void validate() throws IllegalArgumentException {
        for (int i=0; i<20*60*60; i++) {
            System.out.print('.');
            try {
                Thread.currentThread().sleep(1000);
            } catch (InterruptedException e) {
                break;
            }
        }
8) works fine without above code.

https://github.com/olehkisil/development-note
https://circleci.com/gh/olehkisil/commons-csv/8#tests



-----------------------------------------------------------------------------
Case 3: PRODSUP-003:

Dear customer support,

I need to explain how CircleCI works to my boss. I’ve read the docs but I still don’t get it. Can you please explain to me, in your own words, how CircleCI works? Also, it seems like you don’t support .NET builds. Why is that?

--

Adam
=============================================================================

Case 3: PRODSUP-003:

Dear Adam,

  CircleCI is the tool for continuous integration with automated test support. It's created to make development test and delivery process easier. When you are ready with your changes on gitHub CircleCI automatically runs all your configured tests for your project. Also there is possibility of automatic deployment if tests succeed. So we do all your routine work. 
  CircleCI is very universal environment and for most standard projects it works just out of the box. If your project requires any special setup there is very easy way to tune even the most complicated cases.
  We support most popular platforms and technologies. We currently serve 2 mobile platforms and 7 web languages. We always improve our service and work on new features all the time. Please check for updates on our site, we will support .NET also soon.

All information is always available on the site https://circleci.com/docs

Kind regards,
Oleh
Customer Support


 



