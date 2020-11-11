---
ms.openlocfilehash: cc394741e399f4fc54dd67f1736f7027badf4c7d
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507090"
---

### <a name="install-the-sdk"></a><span data-ttu-id="56042-101">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="56042-101">Install the SDK</span></span>

<span data-ttu-id="56042-102">.NET SDK 可讓您使用 .NET 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="56042-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="56042-103">如果您安裝 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="56042-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="56042-104">若要安裝 .NET SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="56042-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo yum install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="56042-105">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="56042-105">Install the runtime</span></span>

<span data-ttu-id="56042-106">ASP.NET Core 執行時間可讓您執行不提供執行時間的 .NET 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="56042-106">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="56042-107">下列命令會安裝 ASP.NET Core 執行時間，也就是最相容的 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="56042-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="56042-108">在您的終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="56042-108">In your terminal, run the following commands:</span></span>

```bash
sudo yum install aspnetcore-runtime-5.0
```

<span data-ttu-id="56042-109">除了 ASP.NET Core 執行時間之外，您還可以安裝 .NET 執行時間，但不包括 ASP.NET Core 支援： `aspnetcore-runtime-5.0` 在先前的命令中將取代為 `dotnet-runtime-5.0` ：</span><span class="sxs-lookup"><span data-stu-id="56042-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo yum install dotnet-runtime-5.0
```
