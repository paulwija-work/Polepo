# Getting Snyk result for Go Package


## Step 1 Downloading required software:
	- Install go 

## Step 2 Setting Environment variable:
	- set your Go env variable : $GOPATH to your desired directory
	~ example: $HOME/go(default)

## Step 3 Creating default directory with a functional dummy Go package:
	- create a new empty directory in $GOPATH/src
	- create a .go file (warning you cannot specify imported go packages versions in the file)

### Dummy Package Script
```

package hello

import ("github.com/cactus/go-camo "
)

func Hello() string {
    return "Hello, world."
}	

``` 
	- create go.mod file with `$ go mod init` will module file which is like a reqiurements.txt in python
	- use '$ go test' to make sure that it is working

## Step 4 Go Package version control:

	- using '$ go get github.com/cactus/go-camo@v1.1.7'
	- it will modify the go.mod file with a require tag that shows the specification of a package version
	~ example:

```
	require (
	github.com/cactus/go-camo v1.1.7 // indirect
	)
```

## Step 5 Creating needed file for Snyk testing:
	- create the vendor folder with '$ go mod vendor'
	- then use the vendor folder and the go.mod file to get Snyk result


## if the module is found but does not contain package:
	~ the reason is that the main github repo have multiple package which contains those .go file
	~ way of solving it would be to import those package separately in the .go file
