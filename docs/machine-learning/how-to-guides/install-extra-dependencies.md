---
title: 安裝額外的 ML.NET 相依性
description: 瞭解如何安裝 ML.NET 套件相依的任何原生程式庫，但不會隨 NuGet 套件一起安裝
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c744b42b4b95681de7b0cbeaef338cc890708fd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008426"
---
# <a name="install-extra-mlnet-dependencies"></a>安裝額外的 ML.NET 相依性

在大部分情況下，在所有作業系統上，安裝 ML.NET 就像參考適當的 NuGet 套件一樣簡單。

```dotnetcli
dotnet add package Microsoft.ML
```

不過在某些情況下，有其他安裝需求，特別是在需要原生元件時。 本檔說明這些案例的安裝需求。 這些區段會依照具有額外相依性的特定 `Microsoft.ML.*` NuGet 套件來細分。

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>時間序列、Microsoft AutoML。

這兩個封裝相依于，相依 `Microsoft.ML.MKL.Redist` 于 `libiomp` 。

### <a name="windows"></a>Windows

不需要額外的安裝步驟。 將 NuGet 套件新增至專案時，會安裝程式庫。

### <a name="linux"></a>Linux

1. 安裝存放庫的 GPG 金鑰

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

2. 新增適用于 MKL 的 APT 存放庫

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

    判斷位置`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    例如：

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. 將此位置新增至載入程式庫路徑：

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. 使用安裝程式庫`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
