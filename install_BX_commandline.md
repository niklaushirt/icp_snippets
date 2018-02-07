## Install BX Command Line

```bash
https://console.bluemix.net/docs/cli/reference/bluemix_cli/all_versions.html#ibm-cloud-cli-installer-all-versions

wget https://clis.ng.bluemix.net/download/bluemix-cli/0.6.4/linux64

tar xvfz linux64

cd Bluemix_CLI/
sudo ./install_bluemix_cli

wget https://192.168.27.199:8443/api/cli/icp-linux-amd64 --no-check-certificate

bx plugin install icp-linux-amd64


bx pr init --host https://mycluster.icp:8443 --skip-ssl-validation
bx pr login -a https://mycluster.icp:8443 --skip-ssl-validation
docker login mycluster.icp:8500

```