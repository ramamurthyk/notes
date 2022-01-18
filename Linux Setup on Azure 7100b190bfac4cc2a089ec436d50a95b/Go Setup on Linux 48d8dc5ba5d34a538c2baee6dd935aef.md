# Go Setup on Linux

Install Go from [https://go.dev/doc/install](https://go.dev/doc/install)

```bash
WGET https://go.dev/dl/go1.17.6.linux-amd64.tar.gz
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.17.6.linux-amd64.tar.gz
```

Now edit the profile settings and add the path.

```bash
sudo vim $HOME/.profile
# At the end of the file, add the below line.
export PATH=$PATH:/usr/local/go/bin
# Save (:wq)
# Now refresh the profile settings.
source $HOME/.profile
```

Verify the installation. Should print the version successfully.

```bash
go version

go version go1.17.6 linux/amd64
```

Create an app and verify.

```bash
mkdir go_app && cd
go mod init hello
go run
```

VS Code Installation.

Install VS Code extension.

[Go - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=golang.Go)

Tools environment configuration after opening a sample go project.

For example:

```
Tools environment: GOPATH=/home/ram/go
Installing 10 tools at /home/ram/go/bin in module mode.
gopkgs
go-outline
gotests
gomodifytags
impl
goplay
dlv
dlv-dap
staticcheck
gopls
```

All tools successfully installed. You are ready to Go 😄

While running a project created via command line, VS code prompts for creation of launch configuration.

For example: launch.json is created as shown below:

```json
{
	"version": "0.2.0",
	"configurations": [
		{
			"name": "Launch Package",
			"type": "go",
			"request": "launch",
			"mode": "auto",
			"program": "${fileDirname}"
		}
	]
}
```