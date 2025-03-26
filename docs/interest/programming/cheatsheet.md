
## 不经常使用就会忘记

### Python

python -m venv <venv_name>  # 通常起名为.venv

<venv_name>\Scripts\activate  # 进入虚拟环境

pip freeze > requirements.txt  # 导出依赖

pip install -r requirements.txt  # 安装依赖

### Anaconda or Miniconda

==Conda 环境管理命令==

| 命令 | 说明 | 示例 |
|------|------|------|
| `conda create -n env_name` | 创建新环境（继承当前 Python 版本） | `conda create -n myenv` |
| `conda create -n env_name python=3.8` | 创建环境并指定 Python 版本 | `conda create -n py38 python=3.8` |
| `conda activate env_name` | 激活环境 | `conda activate py38` |
| `conda deactivate` | 退出当前环境 | `conda deactivate` |
| `conda env list` | 列出所有环境 | `conda env list` |
| `conda remove -n env_name --all` | 删除整个环境 | `conda remove -n oldenv --all` |
| `conda env export > env.yml` | 导出环境配置 | `conda env export > environment.yml` |
| `conda env create -f env.yml` | 从 YAML 文件创建环境 | `conda env create -f env.yml` |

==Conda 包管理命令==

| 命令 | 说明 | 示例 |
|------|------|------|
| `conda install pkg_name` | 安装包 | `conda install numpy` |
| `conda install pkg_name=version` | 安装指定版本包 | `conda install pandas=1.3.5` |
| `conda list` | 列出已安装包 | `conda list` |
| `conda search pkg_name` | 搜索可用包版本 | `conda search tensorflow` |
| `conda update pkg_name` | 更新单个包 | `conda update numpy` |
| `conda update --all` | 更新所有包 | `conda update --all` |
| `conda remove pkg_name` | 卸载包 | `conda remove matplotlib` |
| `conda clean --all` | 清理缓存 | `conda clean --all` |

==Conda Python 版本控制命令==

| 命令 | 说明 | 示例 |
|------|------|------|
| `conda search python` | 查看可用 Python 版本 | `conda search python` |
| `conda install python=version` | 切换环境 Python 版本 | `conda install python=3.7` |
| `conda create --no-default-packages` | 创建空环境（不安装 Python） | `conda create -n empty_env --no-default-packages` |

==Conda 配置与问题排查==

| 命令 | 说明 | 示例 |
|------|------|------|
| `conda config --show` | 显示所有配置 | `conda config --show` |
| `conda config --add channels URL` | 添加镜像源 | `conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/` |
| `conda init shell_name` | 修复激活问题 | `conda init powershell` |
| `conda info` | 查看 conda 信息 | `conda info` |
| `conda create --clone old_env -n new_env` | 克隆环境 | `conda create --clone base -n mybase` |
