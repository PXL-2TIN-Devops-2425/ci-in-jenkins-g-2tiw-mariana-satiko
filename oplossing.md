Vul onderstaande aan met de antwoorden op de vragen uit de readme.md file. Wil je de oplossingen file van opmaak voorzien? Gebruik dan [deze link](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) om informatie te krijgen over
opmaak met Markdown.


a)The first step to be able to use the Jenkinsfile from this repository was to create a pipeline where the script was associated with this file. 
The SSH link to the repository is then entered in the requested field and the branch to be used is specified.
![Screenshot van new Pipeline](img/Pipeline-script-with-SCM.png)

Besides that, it is necessary that my Jenkins has authorized access to my repositories on GitHub. This is why a new authentication was created.
In the "Kind" field we specify that we will use an SSH username with private key and the GitHub account username is entered in the username field.
In the private key field we add our private key.
![Screenshot van new Jenkins Credential](img/New-credential-jenkins.png)

The important step to take into account is that in the private key field we have to provide a private key linked to a public key insert in an SSH key on github.
![Screenshot van new SSh key gitHub](img/SSH-GitHub.png)

These keys were created in the terminal as shown in the screenshot below.
![Screenshot van Public and Private key](img/Public-and-private-key.png)

From now on, whenever the pipeline is built it will use the script in the Jenkinsfile file present in this repository.

b) 
First we install the pludin NodeJS as shown in the screenshot below.
![Screenshot van NodeJSPlugin](img/NodeJsPlugin.png)

We then install NodeJS 23.3.0 and configure it in Jenkins Global Tool Configuration called "TINnode-devops".
![Screenshot van NodeJS Configuratie in TINnode-devops](img/New-NodeJs.png)

c)

Next we need to provide stage to fetch the source code from our personal GitHub repository on the main branch.
![Screenshot van Jenkins file stage](img/stage_getting_source_from_github.png)

Then we create a stage “install dependencies” that will ensure that all npmdependencies of the application will be installed.
![Screenshot van Jenkins file stage to install dependencies](img/install_dependencies_stage.png)

Then we add a stage “unit test” that will perform the unit tests of the application.This will allow to run unit tests using npm test.
junit 'junit.xml' is used for archiving JUnit test results and ensures the test framework generates the report as junit.xml
![Screenshot van unit test stage](img/unit_test_stage.png)

Next, add a stage 'create a bundle' that excludes unnecessary files and creates a bundle.zip with only the required files.
![Screenshot van create bundle stage](img/create_bundle_stage.png)

The next stage ensure failure handling. It writes a failure log with the date and time to /var/lib/jenkins/jenkinserrorlog.
![Screenshot van post failire](img/post_failure.png)

Finally, archiving artifacts.
Archives the bundle.zip as a build artifact when the pipeline runs successfully.
![Screenshot van archiving artifacts](img/success.png)

Not, quite finally yet!
To ensure the pipeline can be executed multiple times without errors, the following adjustments were made:
Before creating a new bundle, clean up any existing artifacts to avoid conflicts.
![Screenshot van cleanup stage](img/cleanup_stage.png)



d)
