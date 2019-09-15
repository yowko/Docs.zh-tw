---
title: 具有元件的程式
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03babe701b46eab54a76094c4728af80e6d9911e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973135"
---
# <a name="program-with-assemblies"></a><span data-ttu-id="cd4d9-102">具有元件的程式</span><span class="sxs-lookup"><span data-stu-id="cd4d9-102">Program with assemblies</span></span>
<span data-ttu-id="cd4d9-103">組件是 .NET Framework 的建置組塊；它們構成部署、版本控制、重複使用、啟用範圍和安全性權限的基礎單位。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="cd4d9-104">組件為通用語言執行平台提供了感知型別實作所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="cd4d9-105">它是建置來共同運作及構成一個功能邏輯單位的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="cd4d9-106">對於執行階段而言，型別不會存在於組件的內容以外。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="cd4d9-107">本節描述如何建立模組、從模組建立組件、建立金鑰組並使用強式名稱來簽署組件，以及將組件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="cd4d9-108">此外，本節還會描述如何使用 [MSIL 反組譯工具 (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件資訊清單資訊。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd4d9-109">從 .NET Framework 2.0 版開始，執行階段不會載入使用 .NET Framework 版本所編譯的組件，而這個版本的版本號碼高於目前載入的執行階段。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="cd4d9-110">這適用於版本號碼的主要與次要元件組合。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd4d9-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="cd4d9-111">In this section</span></span>  
 [<span data-ttu-id="cd4d9-112">建立元件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-112">Create assemblies</span></span>](create.md)  
 <span data-ttu-id="cd4d9-113">提供單一檔案和多檔案組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="cd4d9-114">元件名稱</span><span class="sxs-lookup"><span data-stu-id="cd4d9-114">Assembly names</span></span>](names.md)  
 <span data-ttu-id="cd4d9-115">提供組件命名概觀。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="cd4d9-116">如何：決定元件的完整名稱</span><span class="sxs-lookup"><span data-stu-id="cd4d9-116">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)  
 <span data-ttu-id="cd4d9-117">描述如何決定組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="cd4d9-118">以完全信任的方式執行內部網路應用程式</span><span class="sxs-lookup"><span data-stu-id="cd4d9-118">Run intranet applications in full trust</span></span>](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="cd4d9-119">描述如何指定內部網路共用上完全信任組件的舊版安全性原則。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="cd4d9-120">元件位置</span><span class="sxs-lookup"><span data-stu-id="cd4d9-120">Assembly location</span></span>](location.md)  
 <span data-ttu-id="cd4d9-121">提供在何處尋找組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="cd4d9-122">如何：建立單一檔案元件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-122">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)  
 <span data-ttu-id="cd4d9-123">描述如何建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="cd4d9-124">多檔案元件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-124">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="cd4d9-125">描述建立多檔案組件的原因。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="cd4d9-126">如何：建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-126">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)  
 <span data-ttu-id="cd4d9-127">描述如何建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="cd4d9-128">設定組件屬性</span><span class="sxs-lookup"><span data-stu-id="cd4d9-128">Set assembly attributes</span></span>](set-attributes.md)  
 <span data-ttu-id="cd4d9-129">描述組件屬性和其設定方式。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="cd4d9-130">建立和使用強式名稱的元件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-130">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)  
 <span data-ttu-id="cd4d9-131">描述如何與為何您使用強式名稱來簽署組件，並包括「如何」主題。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="cd4d9-132">延遲簽署元件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-132">Delay-sign an assembly</span></span>](delay-sign.md)  
 <span data-ttu-id="cd4d9-133">描述如何延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="cd4d9-134">使用元件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="cd4d9-134">Work with assemblies and the global assembly cache</span></span>](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="cd4d9-135">描述如何與為何您將組件新增至全域組件快取，並包括「如何」主題。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="cd4d9-136">如何：視圖元件內容</span><span class="sxs-lookup"><span data-stu-id="cd4d9-136">How to: View assembly contents</span></span>](view-contents.md)  
 <span data-ttu-id="cd4d9-137">描述如何使用 MSIL 反組譯工具 (Ildasm.exe) 來檢視組件內容。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="cd4d9-138">Common language runtime 中的類型轉送</span><span class="sxs-lookup"><span data-stu-id="cd4d9-138">Type forwarding in the common language runtime</span></span>](type-forwarding.md)  
 <span data-ttu-id="cd4d9-139">描述如何使用類型轉送將類型移至不同組件，而不會中斷現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cd4d9-140">參考資料</span><span class="sxs-lookup"><span data-stu-id="cd4d9-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="cd4d9-141">代表組件的 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cd4d9-142">相關章節</span><span class="sxs-lookup"><span data-stu-id="cd4d9-142">Related sections</span></span>  
 [<span data-ttu-id="cd4d9-143">如何：從元件中取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="cd4d9-143">How to: Obtain type and member information from an assembly</span></span>](../../framework/reflection-and-codedom/get-type-member-information.md)  
 <span data-ttu-id="cd4d9-144">描述如何以程式設計方式從組件中取得類型和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="cd4d9-145">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-145">Assemblies in .NET</span></span>](index.md)  
 <span data-ttu-id="cd4d9-146">提供 Common Language Runtime 組件的概念性概觀。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="cd4d9-147">元件版本控制</span><span class="sxs-lookup"><span data-stu-id="cd4d9-147">Assembly versioning</span></span>](versioning.md)  
 <span data-ttu-id="cd4d9-148">提供組件繫結以及 <xref:System.Reflection.AssemblyVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性的概觀。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="cd4d9-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="cd4d9-149">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="cd4d9-150">描述執行階段如何決定要用哪個組件來實現繫結要求。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 <span data-ttu-id="cd4d9-151">[反映](../../framework/reflection-and-codedom/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="cd4d9-151">[Reflection](../../framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="cd4d9-152">描述如何使用「反映」類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cd4d9-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
