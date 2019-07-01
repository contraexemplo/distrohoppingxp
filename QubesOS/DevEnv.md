## JavaScript

### Installing yarn on Fedora

Install it using RPM.

`curl --silent --location https://dl.yarnpkg.com/rpm/yarn.repo | sudo tee /etc/yum.repos.d/yarn.repo`

Then you can use either `yum` or `dnf` to install it:

`sudo yum install yarn`

or 

`sudo dnf install yarn`

Reference: https://yarnpkg.com/lang/en/docs/install/#centos-stable
