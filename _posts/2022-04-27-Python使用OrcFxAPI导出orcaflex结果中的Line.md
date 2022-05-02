---
title      : Python 使用 OrcFxAPI 导出 orcaflex 结果中的 Line
date       : 2022-04-27 14:07:51 +0800
tags       : Python orcaflex OrcFxAPI
categories : Python
classes    : wide
---

**OrcFxAPI需要OrcaFlex正版授权**

**OrcFxAPI需要OrcaFlex正版授权**

**OrcFxAPI需要OrcaFlex正版授权**

## 安装 `Python`

具体的操作不做说明。 `OrcaFlex` 和 `Python` 之间的版本对应关系见🔗：[https://www.orcina.com/webhelp/OrcFxAPI/Default.htm](https://www.orcina.com/webhelp/OrcFxAPI/Default.htm)

### 安装 `pandas` 包

保存操作利用到了 `pandas` 包，可直接用 `pip` 进行安装：

```pip
pip install pandas -i https://mirrors.aliyun.com/pypi/simple
```

## 安装OrcFxAPI Python接口

1. 进入到 `%替换你的OrcaFlex安装目录%\OrcFxAPI\Python`目录下
2. 双击运行 `InstallPythonInterface.bat` 文件

## 导出脚本

```python
import OrcFxAPI
import pandas as pd
import os

# 你的文件名
fname = "myFile.sim"
# 要导出的 line 名称
lineName = "line1"

# 要导出的变量名
variableNameList = ["X", "GY acceleration", "GZ acceleration"]
# 导出的时间最小值
periodMin = -50
# 导出的时间最大值
periodMax = 500

# 生成下输出的文件名
tmp = os.path.basename(fname)#带后缀的文件名
outFName = tmp.split('.')[0]#不带后缀的文件名

# 打开文件模型
model = OrcFxAPI.Model(fname)
# 选中到 line
line = model[lineName]

# 循环导出
for variableName in variableNameList:
 for i in range(-50, 500):
  results = line.RangeGraph(variableName, OrcFxAPI.SpecifiedPeriod(i, i))
  data = pd.DataFrame(results.Min)
  csvName = "%s_%s_%s.csv" % (outFName, variableName, i)
  # index参数设置为False表示不保存行索引,header设置为False表示不保存列索引
  data.to_csv(csvName, index=False, header=False)
```
