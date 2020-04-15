mkdate : 2020-04-15
update : 2020-04-15

### Lecture Note

# Django로 순식간에 블로그 만들기

#### 강의 개요

- lecture date : 2016-10-07
- 강의 당시 개발환경 : Git, Python3.6, Homebrew, Atom,, Heroku
- Slide : [PDF File](http://emocon.weirdx.io/2016fw/slides/chiyodad_django-x-heroku.pdf)
- EMOCON 2016 F/W : [Github Archive](https://github.com/weirdmeetup/emocon/tree/gh-pages/2016fw/slides)

### 개발환경 setting

- 강의에서는 macOS - Python3.6 - Django 1.10.2
- 나는 요즘 VSCode Remote-container가 제공하는 Docker preset(Python3-Postgresql)에서 작업 중이라
- Debian 10 - Python 3.8 - Django 3.0.5 사용

```bash
# lsb_release -a
No LSB modules are available.
Distributor ID: Debian
Description:    Debian GNU/Linux 10 (buster)
Release:        10
Codename:       buster
```
## Heroku 
### Install Heroku CLI

- [The Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)

- 나는 Debian 이므로 terminal에서 아래 명령 실행 (Ubuntu의 `snap`으로는 바로 설치 안됨)

```bash
curl https://cli-assets.heroku.com/install.sh | sh
```

- check version

```bash
# heroku --version
heroku/7.39.2 linux-x64 node-v12.13.0
```

### Getting Started

- heroku login 
  - `heroku login` : (basic) browser login
  - `heroku login -i` : docker의 debian에서는 web browser 없으므로 terminal에서 login 진행

```bash
# heroku login -i
heroku: Enter your login credentials
Email: johnwi@knou.ac.kr
Password: *********
Logged in as johnwi@knou.ac.kr
```

- heroku start

```bash
# heroku create gitgitwi-test1
Creating ⬢ gitgitwi-test1... done
https://gitgitwi-test1.herokuapp.com/ | https://git.heroku.com/gitgitwi-test1.git
```

![First Heroku Page](/assets/Screen%20Shot%202020-04-16%20at%2000.58.51.png)

- check info

```bash
# heroku info gitgitwi-test1
=== gitgitwi-test1
Auto Cert Mgmt: false
Dynos:          
Git URL:        https://git.heroku.com/gitgitwi-test1.git
Owner:          johnwi@knou.ac.kr
Region:         us
Repo Size:      0 B
Slug Size:      0 B
Stack:          heroku-18
Web URL:        https://gitgitwi-test1.herokuapp.com/
```

- Heroku - Git 연동 확인
```bash
# git remote
heroku
origin
```

- browser open to visit the site ; Docker에서는 web browser 바로 접속 불가능하므로~
```bash
# heroku open
 ▸    Error opening web browser.
 ▸    Error: Exited with code 3
 ▸    
 ▸    Manually visit https://gitgitwi-test1.herokuapp.com/ in your browser
```

## Start Django Project