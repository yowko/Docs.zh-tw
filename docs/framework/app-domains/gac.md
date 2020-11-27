---
title: 全域組件快取
description: 瞭解全域組件快取，這是安裝適用于 .NET 的 common language runtime 的全電腦程式代碼快取。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 57d18c01bd6261e8207d8ad3849a3a7da9a24b6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264604"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="bf038-103">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="bf038-103">Global Assembly Cache</span></span>

<span data-ttu-id="bf038-104">每部安裝通用語言執行平台的電腦都有稱為「全域組件快取」的全電腦程式碼快取。</span><span class="sxs-lookup"><span data-stu-id="bf038-104">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="bf038-105">全域組件快取會儲存特別指定為由電腦上數個應用程式共用的組件。</span><span class="sxs-lookup"><span data-stu-id="bf038-105">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="bf038-106">您應該只有在需要時才將組件安裝到全域組件快取，來共用組件。</span><span class="sxs-lookup"><span data-stu-id="bf038-106">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="bf038-107">一般來說，除非明確需要共用組件，否則會將組件相依性保留為私用，並且在應用程式目錄中尋找組件。</span><span class="sxs-lookup"><span data-stu-id="bf038-107">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="bf038-108">此外，不需要將組件安裝到全域組件快取，它們即可供 COM Interop 或非受控碼使用。</span><span class="sxs-lookup"><span data-stu-id="bf038-108">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf038-109">有些情況下您明確不想將組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="bf038-109">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="bf038-110">如果您將構成應用程式的其中一個組件放入全域組件快取中，則可以使用 **xcopy** 命令複製應用程式目錄，以不再複寫或安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf038-110">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="bf038-111">您也必須在全域組件快取中移動組件。</span><span class="sxs-lookup"><span data-stu-id="bf038-111">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="bf038-112">將組件部署到全域組件快取的方式有兩種：</span><span class="sxs-lookup"><span data-stu-id="bf038-112">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="bf038-113">使用設計來使用全域組件快取的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="bf038-113">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="bf038-114">這是將組件安裝到全域組件快取慣用的選項。</span><span class="sxs-lookup"><span data-stu-id="bf038-114">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="bf038-115">使用稱為[全域組件快取工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 的開發人員工具，它是由 Windows SDK 所提供。</span><span class="sxs-lookup"><span data-stu-id="bf038-115">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf038-116">在部署案例中，請使用 Windows Installer 將組件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="bf038-116">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="bf038-117">您應該只在開發案例中使用全域組件快取工具，因為它不提供組件參考計數和在使用 Windows 安裝程式時提供的其他功能。</span><span class="sxs-lookup"><span data-stu-id="bf038-117">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="bf038-118">從 .NET Framework 4 開始，全域組件快取的預設位置為 **%windir%\Microsoft.NET\assembly**。</span><span class="sxs-lookup"><span data-stu-id="bf038-118">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="bf038-119">在舊版 .NET Framework 中，預設位置為 **%windir%\assembly**。</span><span class="sxs-lookup"><span data-stu-id="bf038-119">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="bf038-120">系統管理員通常會使用存取控制清單 (ACL) 來控制寫入和執行存取權，以便保護 systemroot 目錄。</span><span class="sxs-lookup"><span data-stu-id="bf038-120">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="bf038-121">因為全域組件快取安裝在 Systemroot 目錄的子目錄中，所以它會繼承該目錄的 ACL。</span><span class="sxs-lookup"><span data-stu-id="bf038-121">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="bf038-122">建議只有具備系統管理員權限的使用者才能從全域組件快取刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="bf038-122">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="bf038-123">全域組件快取中部署的組件都必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="bf038-123">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="bf038-124">將組件新增至全域組件快取時，會對構成組件的所有檔案執行完整性檢查。</span><span class="sxs-lookup"><span data-stu-id="bf038-124">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="bf038-125">快取執行這些完整性檢查，以確保組件並未遭到破壞，比方說，當檔案已經變更，但資訊清單不會反映變更。</span><span class="sxs-lookup"><span data-stu-id="bf038-125">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf038-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf038-126">See also</span></span>

- [<span data-ttu-id="bf038-127">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="bf038-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="bf038-128">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="bf038-128">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="bf038-129">強式名稱的元件</span><span class="sxs-lookup"><span data-stu-id="bf038-129">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
