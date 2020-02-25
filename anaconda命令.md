1. 查看已安装的包

   ```shell
    conda list
   ```

   

2. 更新所有包

   ```shell
    conda upgrade --all
   ```

   

3.  安装包

   ```shell
    conda install package_name
   ```

   

4.  删除包

   ```sehll
    conda remove package_name
   ```

   

5.  更新包

   ```shell
    conda update package_name
   ```

   

6. 不知道包名要找包

   ```shell
    conda search name
   ```

    

7.  用conda建立虚拟环境

   ```shell
    conda create -n env_name  list_of_packages
    # 其中 -n 代表 name，env_name 是需要创建的环境名称，list of packages 则是列出在新环境中需要安装的工具包。
    
     conda create -n data_analysis python=3.7 pandas
   ```

   

8.  进入虚拟环境

   ```shell
    source activate env_name
   ```

   

9.  退出虚拟环境

   ```shell
    source deactivate
   ```

   

10.  删除名为 env_name 的环境

    ```shell
     conda env remove -n env_name
    ```

    

11.  显示所有的环境

    ```
     conda env list
    ```

    

12.  当分享代码的时候，同时也需要将运行环境分享给大家，执行如下命令可以将当前环境下的 package 信息存入名为 environment 的 YAML 文件中

    ```
     conda env export > environment.yaml
    ```

13. 使用别人生成的yaml文件创建环境

    ```shell
     conda env create -f environment.yaml
    ```

    

    