---
ms.openlocfilehash: 87c7abf6a20dd8e9769f3b3b3cbe271d32fd62c3
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506971"
---

### <a name="install-the-sdk"></a><span data-ttu-id="8a494-101">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="8a494-101">Install the SDK</span></span>

<span data-ttu-id="8a494-102">.NET SDK 可讓您使用 .NET 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a494-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="8a494-103">如果您安裝 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="8a494-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="8a494-104">若要安裝 .NET SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8a494-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="8a494-105">如果您收到類似「 **找不到套件 dotnet-sdk-5.0** 」的錯誤訊息，請參閱 [APT 疑難排解](#apt-troubleshooting) 一節。</span><span class="sxs-lookup"><span data-stu-id="8a494-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-5.0** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="8a494-106">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="8a494-106">Install the runtime</span></span>

<span data-ttu-id="8a494-107">ASP.NET Core 執行時間可讓您執行不提供執行時間的 .NET 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a494-107">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="8a494-108">下列命令會安裝 ASP.NET Core 執行時間，也就是最相容的 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="8a494-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="8a494-109">在您的終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8a494-109">In your terminal, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="8a494-110">如果您收到類似「 **找不到封裝 aspnetcore-runtime-5.0** 」的錯誤訊息，請參閱 [APT 疑難排解](#apt-troubleshooting) 一節。</span><span class="sxs-lookup"><span data-stu-id="8a494-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-5.0** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="8a494-111">除了 ASP.NET Core 執行時間之外，您還可以安裝 .NET 執行時間，但不包括 ASP.NET Core 支援： `aspnetcore-runtime-5.0` 在先前的命令中將取代為 `dotnet-runtime-5.0` ：</span><span class="sxs-lookup"><span data-stu-id="8a494-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo apt-get install -y dotnet-runtime-5.0
```
