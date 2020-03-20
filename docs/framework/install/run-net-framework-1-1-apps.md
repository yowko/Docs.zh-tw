---
title: 在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式
description: 描述如何適應需要 .NET 框架 1.1 的應用，這些應用在 Windows 作業系統的許多版本中不再受支援。
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 28bf3669c24fdd8a6bf45f57059c2953c5ab27dd
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506966"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a><span data-ttu-id="056c7-103">在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式</span><span class="sxs-lookup"><span data-stu-id="056c7-103">Run .NET Framework 1.1 apps on Windows 8, Windows 8.1, or Windows 10</span></span>

<span data-ttu-id="056c7-104">Windows 8、Windows 8.1、Windows 伺服器 2012、Windows 伺服器 2012 R2 或 Windows 10 作業系統不支援 .NET 框架 1.1。</span><span class="sxs-lookup"><span data-stu-id="056c7-104">The .NET Framework 1.1 is not supported on the Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2, or the Windows 10 operating systems.</span></span> <span data-ttu-id="056c7-105">在某些情況下，會將 .NET Framework 1.1 明確視為執行應用程式所需的必要項。</span><span class="sxs-lookup"><span data-stu-id="056c7-105">In some cases, the .NET Framework 1.1 is specifically identified as required for an app to run.</span></span> <span data-ttu-id="056c7-106">在這些情況下，您應該連絡您的獨立軟體廠商 (ISV) 將應用程式升級，以便在 .NET Framework 3.5 SP1 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="056c7-106">In those cases, you should contact your independent software vendor (ISV) to have the app upgraded to run on the .NET Framework 3.5 SP1 or later version.</span></span> <span data-ttu-id="056c7-107">如需其他資訊，請參閱[從 .NET Framework 1.1 移轉](../migration-guide/migrating-from-the-net-framework-1-1.md)。</span><span class="sxs-lookup"><span data-stu-id="056c7-107">For additional information, see [Migrating from the .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).</span></span>

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a><span data-ttu-id="056c7-108">從光碟或下載中心安裝 .NET Framework 1.1</span><span class="sxs-lookup"><span data-stu-id="056c7-108">Install the .NET Framework 1.1 from a CD or Download Center</span></span>

<span data-ttu-id="056c7-109">無法在 Windows 8、Windows 8.1、Windows 伺服器 2012、Windows 伺服器 2012 R2 或 Windows 10 上手動安裝 .NET 框架 1.1。</span><span class="sxs-lookup"><span data-stu-id="056c7-109">It isn't possible to manually install the .NET Framework 1.1 on Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2, or Windows 10.</span></span> <span data-ttu-id="056c7-110">它不再受支援。</span><span class="sxs-lookup"><span data-stu-id="056c7-110">It is no longer supported.</span></span> <span data-ttu-id="056c7-111">如果您嘗試安裝該套件，便會顯示下面錯誤訊息：「安裝程式無法繼續，因為這個 .NET Framework 版本與之前安裝的版本不相容」。</span><span class="sxs-lookup"><span data-stu-id="056c7-111">If you try to install the package, the following error message is displayed: "Setup cannot continue because this version of the .NET Framework is incompatible with a previously installed one."</span></span> <span data-ttu-id="056c7-112">若要解決這個問題，請安裝 [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22)。</span><span class="sxs-lookup"><span data-stu-id="056c7-112">To solve this problem, install the [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22).</span></span> <span data-ttu-id="056c7-113">此版本包括 .NET 框架 2.0（.NET 框架 1.1 後面的版本），Windows 8、Windows 8.1 和 Windows 10 上支援該版本。</span><span class="sxs-lookup"><span data-stu-id="056c7-113">This version includes the .NET Framework 2.0 (the release that follows the .NET Framework 1.1), which is supported on Windows 8, Windows 8.1, and Windows 10.</span></span> <span data-ttu-id="056c7-114">您一定要先嘗試安裝應用程式，判斷它是否會自動更新為較新版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="056c7-114">You should always try to install the app first to determine if it will automatically be updated to a later version of the .NET Framework.</span></span> <span data-ttu-id="056c7-115">如果沒有，請連絡您的 ISV 以取得應用程式更新。</span><span class="sxs-lookup"><span data-stu-id="056c7-115">If it does not, contact your ISV for an app update.</span></span>

## <a name="see-also"></a><span data-ttu-id="056c7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="056c7-116">See also</span></span>

- [<span data-ttu-id="056c7-117">從 .NET Framework 1.1 移轉</span><span class="sxs-lookup"><span data-stu-id="056c7-117">Migrating from the .NET Framework 1.1</span></span>](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="056c7-118">在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="056c7-118">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>](dotnet-35-windows-10.md)
