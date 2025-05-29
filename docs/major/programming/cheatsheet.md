
## 不经常使用就会忘记

### Python

| Command| Description| Example|
|---------|-------------|---------|
| `python -m venv venv_name` | 创建虚拟环境 | `python -m venv .venv` |
| `venv_name\Scripts\activate` | 进入虚拟环境 | `.venv\Scripts\activate` |
| `pip freeze > requirements.txt` | 导出依赖 | `pip freeze > requirements.txt` |
| `pip install -r requirements.txt` | 安装依赖 | `pip install -r requirements.txt` |




### Micromamba (same as the conda)

#### Environment Management

| Command| Description| Example|
|------|------|------|
| `mmba create -n env_name` | 创建新环境（继承当前 Python 版本） | `mmba create -n myenv` |
| `mmba create -n env_name python=3.8` | 创建环境并指定 Python 版本 | `mmba create -n py38 python=3.8` |
| `mmba activate env_name` | 激活环境 | `mmba activate py38` |
| `mmba deactivate` | 退出当前环境 | `mmba deactivate` |
| `mmba env list` | 列出所有环境 | `mmba env list` |
| `mmba remove -n env_name --all` | 删除整个环境 | `mmba remove -n oldenv --all` |
| `mmba list --json > env.json` | 导出环境配置，然后手动转换为yml或者脚本处理 | `mmba list --json > environment.json` |
| `mmba env create -f env.yml` | 从 YAML 文件创建环境 | `mmba env create -f env.yml` |

#### Package Management

| Command| Description| Example|
|------|------|------|
| `mmba install pkg_name` | 安装包 | `mmba install numpy` |
| `mmba install pkg_name=version` | 安装指定版本包 | `mmba install pandas=1.3.5` |
| `mmba list` | 列出已安装包 | `mmba list` |
| `mmba search pkg_name` | 搜索可用包版本 | `mmba search tensorflow` |
| `mmba update pkg_name` | 更新单个包 | `mmba update numpy` |
| `mmba update --all` | 更新所有包 | `mmba update --all` |
| `mmba remove pkg_name` | 卸载包 | `mmba remove matplotlib` |
