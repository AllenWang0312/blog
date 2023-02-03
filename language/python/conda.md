pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple somepackage

conda update conda

conda create -n xxxx python=3.5
conda activate xxxx
conda deactivate                  //閸忔娊妫撮悳顖氼暔
conda env list


conda list         #閺屻儳婀呭鑼病鐎瑰顥婇惃鍕瀮娴犺泛瀵�
conda update xxx   #閺囧瓨鏌妜xx閺傚洣娆㈤崠锟�
conda uninstall xxx   #閸楁瓕娴噚xx閺傚洣娆㈤崠锟�

conda remove -n xxxx --all //閸掓稑缂搙xxx閾忔碍瀚欓悳顖氼暔


### conda install 閿熸枻鎷�
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
