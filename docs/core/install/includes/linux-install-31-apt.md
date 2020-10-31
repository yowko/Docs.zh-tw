---
ms.openlocfilehash: 56f5d27eb9be2f8eb3e335c5ec161dba1bcfdb1e
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135783"
---

### <a name="install-the-sdk"></a><span data-ttu-id="ad95b-101">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="ad95b-101">Install the SDK</span></span>

<span data-ttu-id="ad95b-102">.NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad95b-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="ad95b-103">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="ad95b-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="ad95b-104">若要安裝 .NET Core SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ad95b-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="ad95b-105">如果您收到類似「 **找不到套件 dotnet-sdk-3.1** 」的錯誤訊息，請參閱 [APT 疑難排解](#apt-troubleshooting) 一節。</span><span class="sxs-lookup"><span data-stu-id="ad95b-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="ad95b-106">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="ad95b-106">Install the runtime</span></span>

<span data-ttu-id="ad95b-107">.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad95b-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="ad95b-108">下列命令會安裝適用于 .NET Core 的 ASP.NET Core 執行時間，這是最相容的執行時間。</span><span class="sxs-lookup"><span data-stu-id="ad95b-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="ad95b-109">在您的終端機中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="ad95b-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="ad95b-110">如果您收到類似「 **找不到封裝 aspnetcore-runtime-3.1** 」的錯誤訊息，請參閱 [APT 疑難排解](#apt-troubleshooting) 一節。</span><span class="sxs-lookup"><span data-stu-id="ad95b-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="ad95b-111">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `aspnetcore-runtime-3.1` 在先前的命令中將取代為 `dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="ad95b-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
