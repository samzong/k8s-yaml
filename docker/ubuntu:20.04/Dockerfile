# 构建: docker build -t bxk/ubuntu:16.04 .
# 保存: docker commit -m="[feature] update image" -a="bambooxking" 9361ce633ff1 bxk/ubuntu:16.04
# 运行: docker run -v ~/Documents:/workspace -it bxk/ubuntu:16.04

# 指定基础镜像
FROM ubuntu:20.04

# 指定镜像的工作目录
WORKDIR /workspace

# 把文件复制到镜像
ADD sources.list /etc/apt/

# 运行指定的命令
RUN ["apt-get", "update"]
RUN ["apt-get", "install", "zsh", "git", "curl", "wget", "vim", "gcc", "valgrind", "cmake", "automake", "nasm", "libpng-dev", "libjpeg-dev", "net-tools", "python", "python-pip", "-y"]

# 安装 python 子模块
RUN ["pip", "install", "flask", "flask_bootstrap", "flask_moment", "flask_dropzone", "flask_sqlalchemy", "flask_script"]
# RUN ["pip", "install", "numpy", "tensorflow"]
RUN ["pip", "install", "graphviz"]

# 配置 zsh
RUN ["sh", "-c", "\"$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)\"", "-y"]
# 设置主题: vim ~/.zshrc 改主题名: ZSH_THEME="pygmalion"

# 配置自定义环境
# vim ~/.zshrc 最底下加一行: source /workspace/env/docker-ubuntu-env.sh

# 容器启动时执行的命令
CMD ["/bin/zsh"]

# 指定标签
LABEL name="ubuntu:20.04" version="1.0"

# 设置环境变量
ENV TEST_DOCKER_FILE="test Dockerfile"

# 暴露镜像端口
#EXPOSE 8080