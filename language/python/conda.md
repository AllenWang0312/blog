conda update conda

conda create -n xxxx python=3.5
conda activate xxxx
conda deactivate                  //关闭环境
conda env list


conda install --channel https://conda.anaconda.org/anaconda tensorflow=1.8.0


conda list         #查看已经安装的文件包
conda update xxx   #更新xxx文件包
conda uninstall xxx   #卸载xxx文件包

conda remove -n xxxx --all //创建xxxx虚拟环境


### conda install ��
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
