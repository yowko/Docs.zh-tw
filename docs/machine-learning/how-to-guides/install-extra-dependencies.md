---
title: 安裝額外的 ML.NET 依賴項目
description: 瞭解如何安裝ML.NET包依賴於但未隨 NuGet 套件安裝的任何本機庫
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: 0b870542706c065295d48205b7780e568e267ab6
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888299"
---
# <a name="install-extra-mlnet-dependencies"></a>安裝額外的 ML.NET 依賴項目

在大多數情況下,在所有作業系統上安裝ML.NET就像引用相應的 NuGet 包一樣簡單。

```bash
dotnet add package Microsoft.ML
```

但是,在某些情況下,還有其他安裝要求,尤其是在需要本機組件時。 本文檔介紹這些案例的安裝要求。 這些部分按具有附加依賴項的特定`Microsoft.ML.*`NuGet 包細分。

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>微軟.ML.時間系列,微軟.ML.自動ML

這兩個包都依賴於`Microsoft.ML.MKL.Redist`。具有`libiomp`依賴 項。

### <a name="windows"></a>Windows

無需額外的安裝步驟。 將 NuGet 套件添加到專案時,將安裝庫。

### <a name="linux"></a>Linux

1. 安裝儲存函式庫的 GPG 金鑰

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. 新增 MKL 的 APT 儲存函式庫

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. 更新套件

    ```bash
    sudo apt-get update
    ```

4. 安裝 MKL

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    例如：

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    確定位置`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    例如：

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. 將這裡加入為負載庫路徑:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_li
    ```

### <a name="mac"></a>Mac

1. 使用`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
