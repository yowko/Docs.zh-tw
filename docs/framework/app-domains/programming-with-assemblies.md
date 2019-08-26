---
title: 使用組件設計程式
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921426"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="6f625-102">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="6f625-102">Programming with Assemblies</span></span>
<span data-ttu-id="6f625-103">組件是 .NET Framework 的建置組塊；它們構成部署、版本控制、重複使用、啟用範圍和安全性權限的基礎單位。</span><span class="sxs-lookup"><span data-stu-id="6f625-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="6f625-104">組件為通用語言執行平台提供了感知型別實作所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="6f625-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="6f625-105">它是建置來共同運作及構成一個功能邏輯單位的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="6f625-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="6f625-106">對於執行階段而言，型別不會存在於組件的內容以外。</span><span class="sxs-lookup"><span data-stu-id="6f625-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="6f625-107">本節描述如何建立模組、從模組建立組件、建立金鑰組並使用強式名稱來簽署組件，以及將組件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="6f625-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="6f625-108">此外，本節還會描述如何使用 [MSIL 反組譯工具 (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件資訊清單資訊。</span><span class="sxs-lookup"><span data-stu-id="6f625-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f625-109">從 .NET Framework 2.0 版開始，執行階段不會載入使用 .NET Framework 版本所編譯的組件，而這個版本的版本號碼高於目前載入的執行階段。</span><span class="sxs-lookup"><span data-stu-id="6f625-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="6f625-110">這適用於版本號碼的主要與次要元件組合。</span><span class="sxs-lookup"><span data-stu-id="6f625-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f625-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="6f625-111">In This Section</span></span>  
 [<span data-ttu-id="6f625-112">建立組件</span><span class="sxs-lookup"><span data-stu-id="6f625-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="6f625-113">提供單一檔案和多檔案組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="6f625-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="6f625-114">組件名稱</span><span class="sxs-lookup"><span data-stu-id="6f625-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="6f625-115">提供組件命名概觀。</span><span class="sxs-lookup"><span data-stu-id="6f625-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="6f625-116">如何：決定組件的完整名稱</span><span class="sxs-lookup"><span data-stu-id="6f625-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="6f625-117">描述如何決定組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="6f625-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="6f625-118">在完全信任環境下執行內部網路應用程式</span><span class="sxs-lookup"><span data-stu-id="6f625-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="6f625-119">描述如何指定內部網路共用上完全信任組件的舊版安全性原則。</span><span class="sxs-lookup"><span data-stu-id="6f625-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="6f625-120">組件位置</span><span class="sxs-lookup"><span data-stu-id="6f625-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="6f625-121">提供在何處尋找組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="6f625-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="6f625-122">如何：建置單一檔案組件</span><span class="sxs-lookup"><span data-stu-id="6f625-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="6f625-123">描述如何建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="6f625-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="6f625-124">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="6f625-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="6f625-125">描述建立多檔案組件的原因。</span><span class="sxs-lookup"><span data-stu-id="6f625-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="6f625-126">如何：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="6f625-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="6f625-127">描述如何建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="6f625-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="6f625-128">設定組件屬性</span><span class="sxs-lookup"><span data-stu-id="6f625-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="6f625-129">描述組件屬性和其設定方式。</span><span class="sxs-lookup"><span data-stu-id="6f625-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="6f625-130">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="6f625-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="6f625-131">描述如何與為何您使用強式名稱來簽署組件，並包括「如何」主題。</span><span class="sxs-lookup"><span data-stu-id="6f625-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="6f625-132">延遲簽署組件</span><span class="sxs-lookup"><span data-stu-id="6f625-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="6f625-133">描述如何延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="6f625-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="6f625-134">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="6f625-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="6f625-135">描述如何與為何您將組件新增至全域組件快取，並包括「如何」主題。</span><span class="sxs-lookup"><span data-stu-id="6f625-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="6f625-136">如何：檢視組件內容</span><span class="sxs-lookup"><span data-stu-id="6f625-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="6f625-137">描述如何使用 MSIL 反組譯工具 (Ildasm.exe) 來檢視組件內容。</span><span class="sxs-lookup"><span data-stu-id="6f625-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="6f625-138">Common Language Runtime 中的類型轉送</span><span class="sxs-lookup"><span data-stu-id="6f625-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="6f625-139">描述如何使用類型轉送將類型移至不同組件，而不會中斷現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f625-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6f625-140">參考資料</span><span class="sxs-lookup"><span data-stu-id="6f625-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="6f625-141">代表組件的 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="6f625-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f625-142">相關章節</span><span class="sxs-lookup"><span data-stu-id="6f625-142">Related Sections</span></span>  
 [<span data-ttu-id="6f625-143">如何：從組件中取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="6f625-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="6f625-144">描述如何以程式設計方式從組件中取得類型和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="6f625-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="6f625-145">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="6f625-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="6f625-146">提供 Common Language Runtime 組件的概念性概觀。</span><span class="sxs-lookup"><span data-stu-id="6f625-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="6f625-147">組件版本控制</span><span class="sxs-lookup"><span data-stu-id="6f625-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="6f625-148">提供組件繫結以及 <xref:System.Reflection.AssemblyVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性的概觀。</span><span class="sxs-lookup"><span data-stu-id="6f625-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="6f625-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="6f625-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="6f625-150">描述執行階段如何決定要用哪個組件來實現繫結要求。</span><span class="sxs-lookup"><span data-stu-id="6f625-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="6f625-151">反映</span><span class="sxs-lookup"><span data-stu-id="6f625-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="6f625-152">描述如何使用「反映」  類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6f625-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
