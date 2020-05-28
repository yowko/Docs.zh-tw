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
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="d0fc7-103">安裝額外的 ML.NET 相依性</span><span class="sxs-lookup"><span data-stu-id="d0fc7-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="d0fc7-104">在大部分情況下，在所有作業系統上，安裝 ML.NET 就像參考適當的 NuGet 套件一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="d0fc7-105">不過在某些情況下，有其他安裝需求，特別是在需要原生元件時。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="d0fc7-106">本檔說明這些案例的安裝需求。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="d0fc7-107">這些區段會依照具有額外相依性的特定 `Microsoft.ML.*` NuGet 套件來細分。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="d0fc7-108">時間序列、Microsoft AutoML。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="d0fc7-109">這兩個封裝相依于，相依 `Microsoft.ML.MKL.Redist` 于 `libiomp` 。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="d0fc7-110">Windows</span><span class="sxs-lookup"><span data-stu-id="d0fc7-110">Windows</span></span>

<span data-ttu-id="d0fc7-111">不需要額外的安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-111">No extra installation steps required.</span></span> <span data-ttu-id="d0fc7-112">將 NuGet 套件新增至專案時，會安裝程式庫。</span><span class="sxs-lookup"><span data-stu-id="d0fc7-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="d0fc7-113">Linux</span><span class="sxs-lookup"><span data-stu-id="d0fc7-113">Linux</span></span>

1. <span data-ttu-id="d0fc7-114">安裝存放庫的 GPG 金鑰</span><span class="sxs-lookup"><span data-stu-id="d0fc7-114">Install the GPG key for the repository</span></span>

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

2. <span data-ttu-id="d0fc7-115">新增適用于 MKL 的 APT 存放庫</span><span class="sxs-lookup"><span data-stu-id="d0fc7-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="d0fc7-116">更新套件</span><span class="sxs-lookup"><span data-stu-id="d0fc7-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="d0fc7-117">安裝 MKL</span><span class="sxs-lookup"><span data-stu-id="d0fc7-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="d0fc7-118">例如：</span><span class="sxs-lookup"><span data-stu-id="d0fc7-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="d0fc7-119">判斷位置`libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="d0fc7-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="d0fc7-120">例如：</span><span class="sxs-lookup"><span data-stu-id="d0fc7-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="d0fc7-121">將此位置新增至載入程式庫路徑：</span><span class="sxs-lookup"><span data-stu-id="d0fc7-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="d0fc7-122">Mac</span><span class="sxs-lookup"><span data-stu-id="d0fc7-122">Mac</span></span>

1. <span data-ttu-id="d0fc7-123">使用安裝程式庫`Homebrew`</span><span class="sxs-lookup"><span data-stu-id="d0fc7-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
