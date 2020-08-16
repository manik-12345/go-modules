1.First time we have to initialize go module,for this run : 
  go mod init github.com/manik-12345/go-modules //this command will create go.mod file for us.
  nb1:if you got error like this : " go mod init: modules disabled by GO111MODULE=off; see 'go help modules' "  then run
      export GO111MODULE="on" or set env-variable GO111MODULE=on
  nb2:run "ls" for file list and run "cat go.mod" to see the file content.

2.If we want some external dependencies/packages then run : go get [name or url]. ex: go get github.com/beevik/etree
  nb:As a result go.sum file will be generated and remember that we should not edit/change this file content.
  nb:And also the dependency will be added to the go.mod file

3.Some important commands:
  a)go mod tidy  //add or remove dependencies
    nb:This command will install required dependencies and remove unrequired dependencies from go.mod file.
  b)go mod why [dep-name]   //ex: dep-name like:go get github.com/beevik/etree
    nb:Adding reason of a module or why we added a dependency, we can find this by up command.

4.In go.mod file if we can see //indirect comment besides a dependency then,It means this dependency is not required.

5.About some tags:
  go get github.com/beevik/etree        |----/-->these two are same
  go get github.com/beevik/etree@latest |---/

  go get github.com/beevik/etree@v1.3   |--->for specific version

6.To see all the versions of a module : 
  go list -m -versions [mod-name]    //like go.uber.org/zap

7.go mod download  //this command will download all the dependencies those are added into go.mod file.
  go build //this command will download all the dependencies those modules are using in the whole project.

8.If we want to see all the dependencies then run:  
  go list -m all :- View final versions that will be used in a build for all direct and indirect dependencies

9.View available minor and patch upgrades for all direct and indirect dependencies
  go list -u -m all

collected from : https://www.youtube.com/watch?v=Z1VhG7cf83M  and  https://github.com/golang/go/wiki/Modules