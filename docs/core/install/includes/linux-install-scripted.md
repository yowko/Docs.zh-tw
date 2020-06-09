---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602947"
---

<span data-ttu-id="e2c8b-101">[Dotnet-安裝腳本](../../tools/dotnet-install-script.md)會用於**SDK**的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK**.</span></span> <span data-ttu-id="e2c8b-102">您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="e2c8b-103">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-103">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="e2c8b-104">若要安裝目前的版本，這可能不是（LTS）版本，請使用 `-c Current` 參數。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="e2c8b-105">若要安裝 .NET Core 執行時間，而不是 SDK，請使用 `--runtime` 參數。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime
```

<span data-ttu-id="e2c8b-106">您可以藉由變更參數來指定特定版本，以安裝特定版本 `-c` 。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="e2c8b-107">下列命令會安裝 .NET Core SDK 3.1。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="e2c8b-108">如需詳細資訊，請參閱[dotnet-安裝腳本參考](../../tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
