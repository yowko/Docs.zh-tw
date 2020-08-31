---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768389"
---

<span data-ttu-id="845a5-101">[Dotnet 安裝腳本](../../tools/dotnet-install-script.md)用於自動化和非系統管理員安裝的**SDK**和**運行**時間。</span><span class="sxs-lookup"><span data-stu-id="845a5-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="845a5-102">您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="845a5-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="845a5-103">腳本預設會安裝最新的 SDK [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="845a5-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="845a5-104">若要安裝目前版本，這可能不是 (LTS) 版本，請使用 `-c Current` 參數。</span><span class="sxs-lookup"><span data-stu-id="845a5-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="845a5-105">若要安裝 .NET Core 執行時間，而不是 SDK，請使用 `--runtime` 參數。</span><span class="sxs-lookup"><span data-stu-id="845a5-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="845a5-106">您可以藉由修改 `-c` 參數來指定特定版本，以安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="845a5-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="845a5-107">下列命令會安裝 .NET Core SDK 3.1。</span><span class="sxs-lookup"><span data-stu-id="845a5-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="845a5-108">如需詳細資訊，請參閱 [dotnet-安裝腳本參考](../../tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="845a5-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
