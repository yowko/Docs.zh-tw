---
ms.openlocfilehash: 540eebd957ce8ce0928db2bd8317cb220cba30bb
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031750"
---

<span data-ttu-id="b0597-101">[Dotnet 安裝腳本](../../tools/dotnet-install-script.md)用於自動化和非系統管理員安裝的 **SDK** 和 **運行** 時間。</span><span class="sxs-lookup"><span data-stu-id="b0597-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="b0597-102">您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="b0597-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="b0597-103">腳本預設會安裝最新的 SDK [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="b0597-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b0597-104">若要安裝目前版本，這可能不是 (LTS) 版本，請使用 `-c Current` 參數。</span><span class="sxs-lookup"><span data-stu-id="b0597-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="b0597-105">若要安裝 .NET 執行時間，而不是 SDK，請使用 `--runtime` 參數。</span><span class="sxs-lookup"><span data-stu-id="b0597-105">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="b0597-106">您可以藉由修改 `-c` 參數來指定特定版本，以安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="b0597-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="b0597-107">下列命令會安裝 .NET SDK 5.0。</span><span class="sxs-lookup"><span data-stu-id="b0597-107">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="b0597-108">如需詳細資訊，請參閱 [dotnet-安裝腳本參考](../../tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="b0597-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
