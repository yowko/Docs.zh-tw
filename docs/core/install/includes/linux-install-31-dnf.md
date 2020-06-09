---
ms.openlocfilehash: 9ba55c45dc8087c2f7766e5cad32dae97784ffd0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603024"
---

### <a name="install-the-sdk"></a><span data-ttu-id="d65db-101">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="d65db-101">Install the SDK</span></span>

<span data-ttu-id="d65db-102">.NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="d65db-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="d65db-103">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="d65db-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="d65db-104">若要安裝 .NET Core SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d65db-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="d65db-105">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="d65db-105">Install the runtime</span></span>

<span data-ttu-id="d65db-106">.NET Core 執行時間可讓您執行使用 .NET Core 所建立且未包含執行時間的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d65db-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="d65db-107">下列命令會安裝 ASP.NET Core 執行時間，這是適用于 .NET Core 的最相容執行時間。</span><span class="sxs-lookup"><span data-stu-id="d65db-107">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="d65db-108">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d65db-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

<span data-ttu-id="d65db-109">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間：在 `aspnetcore-runtime-3.1` 上述命令中以取代 `dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="d65db-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```
