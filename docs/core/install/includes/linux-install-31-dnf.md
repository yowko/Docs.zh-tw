---
ms.openlocfilehash: 53cac9ca49502c88f5d3cf63bf113365e7b85d18
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507042"
---

### <a name="install-the-sdk"></a><span data-ttu-id="d50d3-101">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="d50d3-101">Install the SDK</span></span>

<span data-ttu-id="d50d3-102">此 .NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="d50d3-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="d50d3-103">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="d50d3-103">If you install the .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="d50d3-104">若要安裝 .NET Core SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d50d3-104">To install the .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="d50d3-105">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="d50d3-105">Install the runtime</span></span>

<span data-ttu-id="d50d3-106">.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d50d3-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="d50d3-107">下列命令會安裝適用于 .NET Core 的 ASP.NET Core 執行時間，這是最相容的執行時間。</span><span class="sxs-lookup"><span data-stu-id="d50d3-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="d50d3-108">在您的終端機中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d50d3-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

<span data-ttu-id="d50d3-109">除了 ASP.NET Core 執行時間之外，您還可以安裝 .NET Core 執行時間（不包括 ASP.NET Core 支援： `aspnetcore-runtime-3.1` 在先前的命令中將取代為） `dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="d50d3-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```
