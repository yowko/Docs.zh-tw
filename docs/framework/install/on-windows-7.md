---
title: 在 Windows 7 SP1 上安裝 .NET Framework
description: 了解如何在 Windows 7 SP1 上安裝 .NET Framework。
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899083"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a><span data-ttu-id="a8159-103">在 Windows 7 SP1 和 Windows Server 2008 R2 上安裝 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8159-103">Install the .NET Framework on Windows 7 SP1 and Windows Server 2008 R2</span></span>

<span data-ttu-id="a8159-104">在 Windows 上執行許多應用程式時需要 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="a8159-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="a8159-105">您可以使用下列指示來安裝它。</span><span class="sxs-lookup"><span data-stu-id="a8159-105">You can use the following instructions to install it.</span></span> <span data-ttu-id="a8159-106">嘗試執行應用程式並在電腦上看到下列對話方塊之後，可能會進入此頁面。</span><span class="sxs-lookup"><span data-stu-id="a8159-106">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![無法啟動這個應用程式](./media/this-application-could-not-be-started.png)

<span data-ttu-id="a8159-108">這些指令將協助您安裝所需的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a8159-108">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="a8159-109">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) 是最新版本。</span><span class="sxs-lookup"><span data-stu-id="a8159-109">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) is the latest version.</span></span> <span data-ttu-id="a8159-110">Windows 7 SP1 和 Windows Server 2008 R2 支援它，並且包含於 [Windows 10 2019 年 5 月更新](https://support.microsoft.com/help/4028685/windows-10-get-the-update)。</span><span class="sxs-lookup"><span data-stu-id="a8159-110">It is supported on Windows 7 SP1 and Windows Server 2008 R2 and is included with [Windows 10 May 2019 Update](https://support.microsoft.com/help/4028685/windows-10-get-the-update).</span></span>

## <a name="net-framework-48"></a><span data-ttu-id="a8159-111">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="a8159-111">.NET Framework 4.8</span></span>

> [!div class="button"]
> [<span data-ttu-id="a8159-112">下載 .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="a8159-112">Download .NET Framework 4.8</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="a8159-113">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) 可用來執行針對 .NET Framework 4.0 或更新版本建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8159-113">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) can be used to run applications built for .NET Framework 4.0 or later.</span></span>

### <a name="offline-installer"></a><span data-ttu-id="a8159-114">離線安裝程式</span><span class="sxs-lookup"><span data-stu-id="a8159-114">Offline installer</span></span>

<span data-ttu-id="a8159-115">在 Windows 7 上進行 .NET Framework 的離線安裝時，必須先確定已在目的電腦上安裝最新的 [Microsoft 根憑證授權單位 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) 。</span><span class="sxs-lookup"><span data-stu-id="a8159-115">When doing an offline install for .NET Framework on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="a8159-116">_certmgr.exe_ 工具可以自動安裝憑證，並從 Visual Studio 或 Windows SDK 取得。</span><span class="sxs-lookup"><span data-stu-id="a8159-116">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="a8159-117">執行 .NET Framework 安裝程式之前，會使用下列命令來安裝憑證：</span><span class="sxs-lookup"><span data-stu-id="a8159-117">The following command is used to install the certificate before running the .NET Framework installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a><span data-ttu-id="a8159-118">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="a8159-118">.NET Framework 3.5</span></span>

<span data-ttu-id="a8159-119">[.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) 隨附於 Windows 7。</span><span class="sxs-lookup"><span data-stu-id="a8159-119">The [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) is included with Windows 7.</span></span>

<span data-ttu-id="a8159-120">.NET Framework 3.5 支援針對 .NET Framework 1.0 到 3.5 建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8159-120">The .NET Framework 3.5 supports apps built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="help"></a><span data-ttu-id="a8159-121">説明</span><span class="sxs-lookup"><span data-stu-id="a8159-121">Help</span></span>

<span data-ttu-id="a8159-122">如果您無法安裝正確的 .NET Framework 版本，可以[連絡 Microsoft 以取得協助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。</span><span class="sxs-lookup"><span data-stu-id="a8159-122">You can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) if you cannot get the correct version of the .NET Framework installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8159-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8159-123">See also</span></span>

- [<span data-ttu-id="a8159-124">下載 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8159-124">Download the .NET Framework</span></span>](https://dotnet.microsoft.com/download)
- [<span data-ttu-id="a8159-125">疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題</span><span class="sxs-lookup"><span data-stu-id="a8159-125">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
- [<span data-ttu-id="a8159-126">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8159-126">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
