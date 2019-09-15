---
title: 使用組件和全域組件快取
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f45f40cd66c63e660b9091c726533dcfe8db086
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971591"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="4625a-102">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="4625a-102">Working with Assemblies and the Global Assembly Cache</span></span>
<span data-ttu-id="4625a-103">如果您想要在數個應用程式之間共用組件，可以將它安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="4625a-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="4625a-104">每部安裝 Common Language Runtime 的電腦都有這個全機器程式碼快取。</span><span class="sxs-lookup"><span data-stu-id="4625a-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="4625a-105">全域組件快取會儲存特別指定為由電腦上數個應用程式共用的組件。</span><span class="sxs-lookup"><span data-stu-id="4625a-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="4625a-106">組件必須有強式名稱，才能安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4625a-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4625a-107">放在全域組件快取中的組件必須具有相同的組件名稱和檔案名稱 (不包括副檔名)。</span><span class="sxs-lookup"><span data-stu-id="4625a-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="4625a-108">例如，組件名稱為 myAssembly 之組件的檔案名稱必須有 myAssembly.exe 或 myAssembly.dll。</span><span class="sxs-lookup"><span data-stu-id="4625a-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
 <span data-ttu-id="4625a-109">您應該只有在必要時才將組件安裝到全域組件快取，來共用組件。</span><span class="sxs-lookup"><span data-stu-id="4625a-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="4625a-110">一般來說，除非明確需要共用組件，否則會將組件相依性保留為私用，並且在應用程式目錄中尋找組件。</span><span class="sxs-lookup"><span data-stu-id="4625a-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="4625a-111">此外，您不需要將組件安裝到全域組件快取，它們即可供 COM Interop 或 Unmanaged 程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="4625a-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
 <span data-ttu-id="4625a-112">您有數個原因想要將組件安裝到全域組件快取中：</span><span class="sxs-lookup"><span data-stu-id="4625a-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="4625a-113">共用位置。</span><span class="sxs-lookup"><span data-stu-id="4625a-113">Shared location.</span></span>  
  
     <span data-ttu-id="4625a-114">應用程式應該使用的組件可以放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4625a-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="4625a-115">例如，如果所有應用程式都應該使用位於全域組件快取中的組件，則可以將版本原則陳述式新增至 Machine.config 檔案，以將參考重新導向至組件。</span><span class="sxs-lookup"><span data-stu-id="4625a-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="4625a-116">檔案安全性。</span><span class="sxs-lookup"><span data-stu-id="4625a-116">File security.</span></span>  
  
     <span data-ttu-id="4625a-117">系統管理員通常會使用存取控制清單 (ACL) 來控制寫入和執行存取權，以便保護 systemroot 目錄。</span><span class="sxs-lookup"><span data-stu-id="4625a-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="4625a-118">因為全域組件快取安裝在 systemroot 目錄中，所以它會繼承該目錄的 ACL。</span><span class="sxs-lookup"><span data-stu-id="4625a-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="4625a-119">建議只有具備系統管理員權限的使用者能從全域組件快取刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="4625a-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="4625a-120">並存版本。</span><span class="sxs-lookup"><span data-stu-id="4625a-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="4625a-121">具有相同名稱但不同版本資訊之組件的多個複本，可以在全域組件快取中進行維護。</span><span class="sxs-lookup"><span data-stu-id="4625a-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="4625a-122">其他搜尋位置。</span><span class="sxs-lookup"><span data-stu-id="4625a-122">Additional search location.</span></span>  
  
     <span data-ttu-id="4625a-123">在探查或使用組態檔中的程式碼基底資訊之前，Common Language Runtime 會檢查全域組件快取中是否有符合組件要求的組件。</span><span class="sxs-lookup"><span data-stu-id="4625a-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="4625a-124">請注意，有些情況下您明確不想要將組件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4625a-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="4625a-125">如果您將構成應用程式的其中一個組件放入全域組件快取中，則可以使用 XCOPY 複製應用程式目錄，以不再複寫或安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="4625a-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="4625a-126">在此情況下，您也必須將組件移至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="4625a-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4625a-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="4625a-127">In This Section</span></span>  
 [<span data-ttu-id="4625a-128">如何：在全域組件快取中安裝單一組件</span><span class="sxs-lookup"><span data-stu-id="4625a-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
 <span data-ttu-id="4625a-129">描述將組件安裝到全域組件快取中的方式。</span><span class="sxs-lookup"><span data-stu-id="4625a-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
 [<span data-ttu-id="4625a-130">如何：檢視全域組件快取的內容</span><span class="sxs-lookup"><span data-stu-id="4625a-130">How to: View the Contents of the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 <span data-ttu-id="4625a-131">說明如何使用 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 來檢視全域組件快取的內容。</span><span class="sxs-lookup"><span data-stu-id="4625a-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="4625a-132">如何：從全域組件快取移除組件</span><span class="sxs-lookup"><span data-stu-id="4625a-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 <span data-ttu-id="4625a-133">說明如何使用 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 來移除全域組件快取中的組件。</span><span class="sxs-lookup"><span data-stu-id="4625a-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
 [<span data-ttu-id="4625a-134">使用 Serviced 元件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="4625a-134">Using Serviced Components with the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 <span data-ttu-id="4625a-135">說明 Serviced 元件 (Managed COM+ 元件) 為何應該放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4625a-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4625a-136">相關章節</span><span class="sxs-lookup"><span data-stu-id="4625a-136">Related Sections</span></span>  
 [<span data-ttu-id="4625a-137">建立組件</span><span class="sxs-lookup"><span data-stu-id="4625a-137">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
 <span data-ttu-id="4625a-138">提供建立組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="4625a-138">Provides an overview of creating assemblies.</span></span>  
  
 [<span data-ttu-id="4625a-139">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="4625a-139">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 <span data-ttu-id="4625a-140">描述全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="4625a-140">Describes the global assembly cache.</span></span>  
  
 [<span data-ttu-id="4625a-141">如何：檢視組件內容</span><span class="sxs-lookup"><span data-stu-id="4625a-141">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
 <span data-ttu-id="4625a-142">說明如何使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件中的 Microsoft 中繼語言 (MSIL) 資訊。</span><span class="sxs-lookup"><span data-stu-id="4625a-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
 [<span data-ttu-id="4625a-143">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="4625a-143">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="4625a-144">描述 Common Language Runtime 如何找出和載入構成應用程式的組件。</span><span class="sxs-lookup"><span data-stu-id="4625a-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="4625a-145">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="4625a-145">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
 <span data-ttu-id="4625a-146">描述組件，即 Managed 應用程式的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="4625a-146">Describes assemblies, the building blocks of managed applications.</span></span>
