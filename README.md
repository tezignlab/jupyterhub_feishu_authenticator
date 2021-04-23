![](https://img.shields.io/badge/PYPI-0.0.1-orange.svg) ![](https://img.shields.io/badge/python-3.6%2B-blue.svg)

# JupyterHub FeiShu OAuthenticator
JupyterHub FeiShu Authenticator is a FeiShu OAuth authenticator built on top of [OAuthenticator](https://github.com/jupyterhub/oauthenticator).


## Installing

feishuoauthenticator is a package available on PyPI and can be installed using pip or cloning the repository.

```
pip3 install feishuoauthenticator
```

or clone the repository

```
git clone https://github.com/tezignlab/jupyterhub_feishu_authenticator.git

cd jupyterhub_feishu_authenticator

pip3 install -e .
```


## Setup

**Step 1:** Create FeiShu App

Please see the FeiShu doc [Create a custom app](https://open.feishu.cn/document/uQjL04CN/ukzM04SOzQjL5MDN)

**Step 2:** Config Your FeiShu App

Go to FeiShu Developer Console --> "Security Settings" --> "Redirect URL", add `http://[your-host]/hub/oauth_callback`

![](https://user-images.githubusercontent.com/595772/114486465-f675f200-9bdb-11eb-87cf-49eb1a13e60f.png)


**Step 3:** Edit JupyterHub Config File `jupyterhub_config.py`

```python
from feishuoauthenticator import FeiShuOAuthenticator
c.JupyterHub.authenticator_class = FeiShuOAuthenticator

app_id = '[your-feishu-app-id]'
app_secret = '[your-feishu-app-secret]'
c.FeiShuOAuthenticator.authorize_url = 'https://open.feishu.cn/open-apis/authen/v1/index'
c.FeiShuOAuthenticator.extra_authorize_params = {'redirect_uri': 'http://[your-host]/hub/oauth_callback', 'app_id': app_id}
c.FeiShuOAuthenticator.client_id = app_id
c.FeiShuOAuthenticator.client_secret = app_secret
```


## Team

- [Harry Wang](http://harrywang.me/)
- [Anoyi](https://anoyi.com)
- Qiang Ju, Tezign.com

