---
title: 在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式
description: 描述如何適應需要 .NET 框架 1.1 的應用，Windows 作業系統的許多版本不再支援 .NET 框架 1.1。
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 6d1cb2f9251bba96d0a378bf4dbab9f7da267037
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111786"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a><span data-ttu-id="eac04-103">在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式</span><span class="sxs-lookup"><span data-stu-id="eac04-103">Run .NET Framework 1.1 apps on Windows 8, Windows 8.1, or Windows 10</span></span>

<span data-ttu-id="eac04-104">在 Windows 8、Windows 8.1、Windows 伺服器 2012、Windows 伺服器 2012 R2 或 Windows 10 作業系統上不支援 .NET 框架 1.1。</span><span class="sxs-lookup"><span data-stu-id="eac04-104">.NET Framework 1.1 is not supported on the Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2, or the Windows 10 operating systems.</span></span> <span data-ttu-id="eac04-105">在某些情況下，需要 .NET 框架 1.1 才能運行應用。</span><span class="sxs-lookup"><span data-stu-id="eac04-105">In some cases, .NET Framework 1.1 is required for an app to run.</span></span> <span data-ttu-id="eac04-106">在這些情況下，請與您的獨立軟體廠商 （ISV） 聯繫，將應用升級到在 .NET 框架 3.5 SP1 或更高版本中運行。</span><span class="sxs-lookup"><span data-stu-id="eac04-106">In those cases, contact your independent software vendor (ISV) to have the app upgraded to run on .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="eac04-107">有關詳細資訊，請參閱從[.NET 框架 1.1 進行遷移](../migration-guide/migrating-from-the-net-framework-1-1.md)。</span><span class="sxs-lookup"><span data-stu-id="eac04-107">For more information, see [Migrating from .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).</span></span>

## <a name="install-net-framework-11-from-a-cd-or-download-center"></a><span data-ttu-id="eac04-108">從 CD 或下載中心安裝 .NET 框架 1.1</span><span class="sxs-lookup"><span data-stu-id="eac04-108">Install .NET Framework 1.1 from a CD or download center</span></span>

<span data-ttu-id="eac04-109">無法在 Windows 8、Windows 8.1、Windows 伺服器 2012、Windows 伺服器 2012 R2 或從 CD 或下載中心手動安裝 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="eac04-109">It isn't possible to manually install .NET Framework 1.1 on Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2, or Windows 10 from a CD or download center.</span></span> <span data-ttu-id="eac04-110">它不再受支援。</span><span class="sxs-lookup"><span data-stu-id="eac04-110">It's no longer supported.</span></span> <span data-ttu-id="eac04-111">如果您嘗試安裝該套件，便會顯示下面錯誤訊息：「安裝程式無法繼續，因為這個 .NET Framework 版本與之前安裝的版本不相容」。</span><span class="sxs-lookup"><span data-stu-id="eac04-111">If you try to install the package, the following error message is displayed: "Setup cannot continue because this version of the .NET Framework is incompatible with a previously installed one."</span></span> <span data-ttu-id="eac04-112">要解決此問題，請安裝[.NET 框架 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22)。</span><span class="sxs-lookup"><span data-stu-id="eac04-112">To solve this problem, install [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22).</span></span> <span data-ttu-id="eac04-113">此版本包括 .NET 框架 2.0（以下版本 .NET 框架 1.1），Windows 8、Windows 8.1 和 Windows 10 支援。</span><span class="sxs-lookup"><span data-stu-id="eac04-113">This version includes .NET Framework 2.0 (the release that follows .NET Framework 1.1), which is supported on Windows 8, Windows 8.1, and Windows 10.</span></span> <span data-ttu-id="eac04-114">您應該始終嘗試先安裝應用，以確定它是否將自動更新為更高版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="eac04-114">You should always try to install the app first to determine if it will automatically be updated to a later version of .NET Framework.</span></span> <span data-ttu-id="eac04-115">如果沒有，請與 ISV 聯繫以進行應用更新。</span><span class="sxs-lookup"><span data-stu-id="eac04-115">If it doesn't, contact your ISV for an app update.</span></span>

## <a name="see-also"></a><span data-ttu-id="eac04-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eac04-116">See also</span></span>

- [<span data-ttu-id="eac04-117">從 .NET Framework 1.1 移轉</span><span class="sxs-lookup"><span data-stu-id="eac04-117">Migrating from the .NET Framework 1.1</span></span>](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="eac04-118">在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="eac04-118">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>](dotnet-35-windows-10.md)
