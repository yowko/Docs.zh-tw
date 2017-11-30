---
title: "發出動態方法和組件"
ms.custom: 
ms.date: 08/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91b0cc4614834f2ad8f7b54d9364d484ca9a6990
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="b58c0-102">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="b58c0-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="b58c0-103">本節說明 <xref:System.Reflection.Emit> 命名空間中的一組 Managed 類型，它可讓編譯器或工具在執行階段發出中繼資料和 Microsoft 中繼語言 (MSIL)，以及選擇性地在磁碟上產生可攜式執行檔 (PE)。</span><span class="sxs-lookup"><span data-stu-id="b58c0-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="b58c0-104">指令碼引擎和編譯器是此命名空間的主要使用者。</span><span class="sxs-lookup"><span data-stu-id="b58c0-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="b58c0-105">在本節中，<xref:System.Reflection.Emit> 命名空間所提供的功能稱為反映發出。</span><span class="sxs-lookup"><span data-stu-id="b58c0-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="b58c0-106">反映發出提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="b58c0-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="b58c0-107">使用 <xref:System.Reflection.Emit.DynamicMethod> 類別，在執行階段定義輕量型全域方法，並使用委派加以執行。</span><span class="sxs-lookup"><span data-stu-id="b58c0-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="b58c0-108">在執行階段定義組件，然後加以執行，並/或儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="b58c0-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="b58c0-109">在執行階段定義組件、加以執行，然後將其卸載，並允許記憶體回收，以回收其資源。</span><span class="sxs-lookup"><span data-stu-id="b58c0-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="b58c0-110">在執行階段定義新組件中的模組，然後加以執行，並/或儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="b58c0-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="b58c0-111">在執行階段定義模組中的類型、建立這些類型的執行個體，並叫用其方法。</span><span class="sxs-lookup"><span data-stu-id="b58c0-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="b58c0-112">針對已定義的模組，定義可供工具 (例如偵錯工具和程式碼分析工具) 使用的符號資訊。</span><span class="sxs-lookup"><span data-stu-id="b58c0-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="b58c0-113">除了 <xref:System.Reflection.Emit> 命名空間中的 Managed 類型，還有[中繼資料介面](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)參考文件中說明的 Unmanaged 中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="b58c0-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="b58c0-114">相較於 Unmanaged 中繼資料介面，Managed 反映發出提供較強的語意錯誤檢查，以及抽象層級較高的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b58c0-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="b58c0-115">另一項適用於中繼資料和 MSIL 的有用資源，是通用語言基礎結構 (CLI) 文件，尤其是＜第二部分：中繼資料定義和語意＞以及＜第三部分：CIL 指令集＞。</span><span class="sxs-lookup"><span data-stu-id="b58c0-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="b58c0-116">您可以在 [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) 以及 [Ecma 網站](http://go.microsoft.com/fwlink/?LinkId=116487)上，線上取得這份文件。</span><span class="sxs-lookup"><span data-stu-id="b58c0-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b58c0-117">本章節內容</span><span class="sxs-lookup"><span data-stu-id="b58c0-117">In This Section</span></span>
  
[<span data-ttu-id="b58c0-118">反映發出中的安全性問題</span><span class="sxs-lookup"><span data-stu-id="b58c0-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="b58c0-119">說明有關使用反映發出來建立動態組件的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="b58c0-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="b58c0-120">[如何： 定義及執行動態方法](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="b58c0-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="b58c0-121">示範如何執行簡單的動態方法和繫結至類別的執行個體的動態方法。</span><span class="sxs-lookup"><span data-stu-id="b58c0-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="b58c0-122">[如何： 定義泛型類型使用反映發出](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="b58c0-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="b58c0-123">示範如何建立簡單的泛型型別具有兩個型別參數、 如何將類別、 介面和特殊條件約束套用至型別參數，以及如何建立類別的型別參數做為參數型別和傳回型別的 memers。</span><span class="sxs-lookup"><span data-stu-id="b58c0-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create memers that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="b58c0-124">[如何： 定義泛型方法使用反映發出](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="b58c0-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="b58c0-125">示範如何建立、 發出，並叫用簡單的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="b58c0-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="b58c0-126">[動態類型產生可回收組件](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="b58c0-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="b58c0-127">導入了可回收組件，也就是動態組件，而不卸載它們建立所在的應用程式定義域可以卸載。</span><span class="sxs-lookup"><span data-stu-id="b58c0-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="b58c0-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="b58c0-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="b58c0-129">將可用來建置方法主體的 MSIL 指令碼編製目錄。</span><span class="sxs-lookup"><span data-stu-id="b58c0-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="b58c0-130">包含用來發出動態方法、組件和類型的 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="b58c0-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="b58c0-131">說明 <xref:System.Type> 類別，其代表 Managed 反映和反映發出中的類型，且其為使用這些技術的關鍵。</span><span class="sxs-lookup"><span data-stu-id="b58c0-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="b58c0-132">包含用來探索中繼資料和 Managed 程式碼的 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="b58c0-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b58c0-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="b58c0-133">Related Sections</span></span>  
 [<span data-ttu-id="b58c0-134">反映</span><span class="sxs-lookup"><span data-stu-id="b58c0-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="b58c0-135">說明如何探索中繼資料和 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b58c0-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="b58c0-136">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="b58c0-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="b58c0-137">提供.NET 實作中的組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="b58c0-137">Provides an overview of assemblies in .NET implementations.</span></span>
