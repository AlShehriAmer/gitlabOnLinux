# gitlabOnLinux
Install gitlab on oracle linux


- Modify ID in */etc/os_release* from `ol` to `centos` or `redhat`

*The os_release file will be like:*

````

NAME="Oracle Linux Server"
VERSION="8.5"
ID="centos"
ID_LIKE="fedora"
VARIANT="Server"
VARIANT_ID="server"
VERSION_ID="8.5"
PLATFORM_ID="platform:el8"
PRETTY_NAME="Oracle Linux Server 8.5"
ANSI_COLOR="0;31"
CPE_NAME="cpe:/o:oracle:linux:8:5:server"
HOME_URL="https://linux.oracle.com/"
BUG_REPORT_URL="https://bugzilla.oracle.com/"

ORACLE_BUGZILLA_PRODUCT="Oracle Linux 8"
ORACLE_BUGZILLA_PRODUCT_VERSION=8.5
ORACLE_SUPPORT_PRODUCT="Oracle Linux"
ORACLE_SUPPORT_PRODUCT_VERSION=8.5


````


- Install dependencies

`yum -y in policycoreutils python3-policycoreutils curl`


- Add Gitlab Repo:

`curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | bash`


* Install Gitlab-ce and configure URL later

`yum install gitlab-ce`

### OR 

* Install Gitlab with URL confguration

`EXTERNAL_URL="http://gitlab.example.com" dnf install -y gitlab-ce`


\* Run the next commands *for oracle docker img* before move 

### *Docker only
`yum install hostname`



- Reconfigure and start Gitlab 

open new terminal session and start `runsvdir` 
`/opt/gitlab/embedded/bin/runsvdir-start`
 and run:
`gitlab-ctl reconfigure`


Move into you browser wite URL of gitlab to sigin-in with root and password you can find it in 
`/etc/gitlab/initial_root_password`
\* you can change your password by running:
`gitlab-rake "gitlab:password:reset"`





