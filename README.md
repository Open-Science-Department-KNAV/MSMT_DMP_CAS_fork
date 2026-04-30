# MŠMT DMP

This data management plan (DMP) template was developed to be use for project
calls of the [Ministry of Education Youth and Sport](https://msmt.gov.cz/?lang=2). It 
can be used with [Data Stewardship Wizard (DSW)](https://ds-wizard.org/) DMP 
tool.


## Usage

This template is available through  [DSW Registry](https://registry.ds-wizard.org/document-templates) 
and also through the [DSW Document Template MŠMT GitLab repository](https://gitlab.ics.muni.cz/fr-cesnet-756-2024/dsw-document-template-msmt.git).

### Contributors

* **Michal Růžička** <[ruzicka@ics.muni.cz](mailto:ruzicka@ics.muni.cz)>
  * ORCID: [0000-0001-5547-8720](https://orcid.org/0000-0001-5547-8720)
* **Peter Janků** <[janku@utb.cz](mailto:janku@utb.cz)>
  * ORCID: [0000-0003-2899-3246](https://orcid.org/0000-0003-2899-3246)
  * GitHub: [@pjanku](https://github.com/pjanku)
* **Marek Suchánek** <[marek.suchanek@ds-wizard.org](mailto:marek.suchanek@ds-wizard.org)>
  * ORCID: [0000-0001-7525-9218](https://orcid.org/0000-0001-7525-9218)
  * GitHub: [@MarekSuchanek](https://github.com/MarekSuchanek)
* **Kryštof Komanec** <[krystof.komanec@ds-wizard.org](mailto:krystof.komanec@ds-wizard.org)>
  * ORCID: [0000-0003-3856-1682](https://orcid.org/0000-0003-3856-1682)
  * GitHub: [@krystofkomanec](https://github.com/krystofkomanec)
* **Jana Martínková** <[jana.martinkova@ds-wizard.org](mailto:jana.martinkova@ds-wizard.org)>
  * ORCID: [0000-0001-8575-6533](https://orcid.org/0000-0001-8575-6533/)
  * GitHub: [@jmartinkova](https://github.com/jmartinkova)

Adapted for CAS by
* **Tereza Kolmačková** <[kolmackova@knav.cz](mailto:kolmackova@knav.cz)>
  * ORCID: [0000-0003-0829-0770](https://orcid.org/0000-0003-0829-0770/)
  * GitHub: [@TerezaKolmackova](https://github.com/TerezaKolmackova)


## Changelog

### 2.2.0

- Updated according to fw:common-horizon-europe-dmp:1.21.0
- released 2026-04-30

### 2.1.1

- Fixed refrence.docx and logo
- released 2026-01-22

### 2.1.0

- New CAS fork based on Horizon Europe DMP 1.20.0
- all changes for CAS fork implemented again
- released 2026-01-14

### 2.0.8
- Fixed macro for ASEP integrations
- released 2025-10-23

### 2.0.7

- Updated according to fw:common-horizon-europe-dmp:1.16.0 - 1.17.0 - 1.18.0
- released 2025-10-10

### 2.0.6
- Deleted reference X non-reference datasets
- Fixed Contributor roles (in ch. 4 Allocation of resources)
- *released 2025-08-25*

### 2.0.5
- Updated according to fw:common-horizon-europe-dmp:1.15.0
- *released 2025-08-01*

### 2.0.4
- Minor changes in contributors
- *released 2025-07-25*

### 2.0.3
- Minor changes in contributors and 02-1-findable.html.j2
- *released 2025-07-23*

### 2.0.2
- Fixed projects reply in Ethics
- *released 2025-05-23*

### 2.0.0 & 2.0.1
- Adapted for CAS
- *released 2025-04-28*

### 1.1.0
- added ORCID integration
- added new role: Creator of DMP
- *released 2025-04-28*

### 1.0.0
- The first official release
- Release 1.0.0


## Development

### Setting up dev environment

For DSW Template development you will need [DSW-TDK](https://guide.ds-wizard.org/en/4.0/more/development/document-templates/tdk.html).

We recommend to install using Python Virtual Environemnt:
```bash
python3 -m venv venv/dsw-tdk
. venv/dsw-tdk/bin/activate
pip install --upgrade pip
pip install dsw-tdk
```

The environment is active only for the current terminal session. Can by 
activated using commmand `. venv/dsw-tdk/bin/activate` in the terminal. And 
deactivated using command `deactivate` in the terminal.

### Packing release

The release can be packed with dsw-tdk environment activated as follows:
```bash
export RELEASE_VERSION=x.y.z
dsw-tdk package -f -o releases/dsw-document-template-msmt-v"${RELEASE_VERSION}".zip
```

Alternatively, you can extract the version info directly from `template.json` 
using [jq utility](https://github.com/jqlang/jq):
```bash
dsw-tdk package -f -o releases/dsw-document-template-msmt-v"$(jq -r .version template.json)".zip
```

#### Publishing release

After commiting all the changes for the new release, create the Git tag and 
push it to the upsteram repository:
```bash
export RELEASE_VERSION="$(jq -r .version template.json)"

git tag -a v"${RELEASE_VERSION}" -m "Release v${RELEASE_VERSION}"
git push origin v"${RELEASE_VERSION}"
```

It is recommended to [cryptographicaly sign the tags](https://git-scm.com/book/cs/v2/Git-Tools-Signing-Your-Work).
You can do so using option `-s` instead of `-a` with the `git tag` command:
```bash
git tag -s v"${RELEASE_VERSION}" -m "Release v${RELEASE_VERSION}"
```
Alternatively to GPG, you can also sign using [SSH keys](https://docs.gitlab.com/ee/user/project/repository/signed_commits/ssh.html)
and [X.509 certificates](https://docs.gitlab.com/ee/user/project/repository/signed_commits/x509.html).

Consequently, you can verify integrity of the commit using
```bash
git tag -v v"${RELEASE_VERSION}"
```

## Origin

The template v1.0.0 was based on [DSW Horizon Europe DMP Template](https://github.com/ds-wizard/horizon-europe-dmp-template)
(forked from [v1.14.0](https://github.com/ds-wizard/horizon-europe-dmp-template/commit/e76d8ae605bc76ead1953d2586920b146b04ceaa))

### Base repository

The base repository the template was forked from can be added with command:
```bash
git remote add "dsw-template-horizon-europe" "git@github.com:ds-wizard/horizon-europe-dmp-template.git"
```
