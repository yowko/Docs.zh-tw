---
ms.openlocfilehash: 36f1ee26def82d426b6637ae96f382fc89791a2f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135908"
---

### <a name="install-the-sdk"></a><span data-ttu-id="0c767-101">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="0c767-101">Install the SDK</span></span>

<span data-ttu-id="0c767-102">此 .NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c767-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="0c767-103">若要安裝 .NET Core SDK，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0c767-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="0c767-104">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="0c767-104">Install the runtime</span></span>

<span data-ttu-id="0c767-105">.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c767-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="0c767-106">下列命令會安裝適用于 .NET Core 的 ASP.NET Core 執行時間，這是最相容的執行時間。</span><span class="sxs-lookup"><span data-stu-id="0c767-106">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="0c767-107">在您的終端機中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0c767-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="0c767-108">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `aspnetcore-runtime-2.1` 在先前的命令中將取代為 `dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="0c767-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
