---
ms.openlocfilehash: b6f2af7af77398d5e902aae995590b5dde4cf76a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602905"
---

### <a name="install-the-sdk"></a><span data-ttu-id="0e74d-101">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="0e74d-101">Install the SDK</span></span>

<span data-ttu-id="0e74d-102">.NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e74d-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="0e74d-103">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e74d-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="0e74d-104">若要安裝 .NET Core SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0e74d-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="0e74d-105">如果您收到類似 [**找不到封裝 dotnet-sdk-3.1**] 的錯誤訊息，請參閱[APT 疑難排解](#apt-troubleshooting)一節。</span><span class="sxs-lookup"><span data-stu-id="0e74d-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="0e74d-106">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="0e74d-106">Install the runtime</span></span>

<span data-ttu-id="0e74d-107">.NET Core 執行時間可讓您執行使用 .NET Core 所建立且未包含執行時間的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e74d-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="0e74d-108">下列命令會安裝 ASP.NET Core 執行時間，這是適用于 .NET Core 的最相容執行時間。</span><span class="sxs-lookup"><span data-stu-id="0e74d-108">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="0e74d-109">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0e74d-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="0e74d-110">如果您收到類似 [**找不到套件 aspnetcore-執行時間-3.1**] 的錯誤訊息，請參閱[APT 疑難排解](#apt-troubleshooting)一節。</span><span class="sxs-lookup"><span data-stu-id="0e74d-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="0e74d-111">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間：在 `aspnetcore-runtime-3.1` 上述命令中以取代 `dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="0e74d-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
