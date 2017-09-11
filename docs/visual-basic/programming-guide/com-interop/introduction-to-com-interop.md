---
title: "COM Interop (Visual Basic) 簡介 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interop assemblies
- COM interop, about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6a50a89db3f24d7e34c1fc683b5f712f3a6992bf
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="introduction-to-com-interop-visual-basic"></a><span data-ttu-id="0fcee-102">COM Interop 簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fcee-102">Introduction to COM Interop (Visual Basic)</span></span>
<span data-ttu-id="0fcee-103">元件物件模型 (COM) 可讓您公開其功能給其他元件和主應用程式的物件。</span><span class="sxs-lookup"><span data-stu-id="0fcee-103">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="0fcee-104">雖然已 Windows 程式設計多年的基礎 COM 物件，如 common language runtime (CLR) 所設計的應用程式有許多好處。</span><span class="sxs-lookup"><span data-stu-id="0fcee-104">While COM objects have been fundamental to Windows programming for many years, applications designed for the common language runtime (CLR) offer many advantages.</span></span>  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]<span data-ttu-id="0fcee-105">應用程式最終會取代開發的 com。</span><span class="sxs-lookup"><span data-stu-id="0fcee-105"> applications will eventually replace those developed with COM.</span></span> <span data-ttu-id="0fcee-106">在那之前，您可能要使用或建立 COM 物件使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0fcee-106">Until then, you may have to use or create COM objects by using [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].</span></span> <span data-ttu-id="0fcee-107">與 COM 互通性或*COM interop*，可讓您使用現有的 COM 物件時，轉換到[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]您自己的步調。</span><span class="sxs-lookup"><span data-stu-id="0fcee-107">Interoperability with COM, or *COM interop*, enables you to use existing COM objects while transitioning to the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] at your own pace.</span></span>  
  
 <span data-ttu-id="0fcee-108">使用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]建立 COM 元件，您可以使用免註冊 COM interop。</span><span class="sxs-lookup"><span data-stu-id="0fcee-108">By using the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] to create COM components, you can use registration-free COM interop.</span></span> <span data-ttu-id="0fcee-109">這可讓您控制當多個版本的電腦上，安裝並可讓使用者可以使用 XCOPY 或 FTP 將您的電腦上的適當目錄的應用程式可以執行它要啟用哪個 DLL 版本。</span><span class="sxs-lookup"><span data-stu-id="0fcee-109">This lets you control which DLL version is enabled when more than one version is installed on a computer, and lets end users use XCOPY or FTP to copy your application to an appropriate directory on their computer where it can be run.</span></span> <span data-ttu-id="0fcee-110">如需詳細資訊，請參閱[免註冊 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)。</span><span class="sxs-lookup"><span data-stu-id="0fcee-110">For more information, see [Registration-Free COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).</span></span>  
  
## <a name="managed-code-and-data"></a><span data-ttu-id="0fcee-111">Managed 程式碼和資料</span><span class="sxs-lookup"><span data-stu-id="0fcee-111">Managed Code and Data</span></span>  
 <span data-ttu-id="0fcee-112">程式碼開發的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]稱為*managed 程式碼*，並包含可由 CLR 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0fcee-112">Code developed for the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] is referred to as *managed code*, and contains metadata that is used by CLR.</span></span> <span data-ttu-id="0fcee-113">所使用的資料[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式會呼叫*管理資料*因為執行階段會管理資料相關工作，例如配置與回收記憶體，以及執行型別檢查。</span><span class="sxs-lookup"><span data-stu-id="0fcee-113">Data used by [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications is called *managed data* because the runtime manages data-related tasks such as allocating and reclaiming memory and performing type checking.</span></span> <span data-ttu-id="0fcee-114">根據預設，[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]使用 managed 程式碼和資料，但您可以存取 unmanaged 程式碼和資料的 COM 物件使用 interop 組件 （在此頁面稍後說明）。</span><span class="sxs-lookup"><span data-stu-id="0fcee-114">By default, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] uses managed code and data, but you can access the unmanaged code and data of COM objects using interop assemblies (described later on this page).</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="0fcee-115">組件</span><span class="sxs-lookup"><span data-stu-id="0fcee-115">Assemblies</span></span>  
 <span data-ttu-id="0fcee-116">組件是主要建置組塊的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fcee-116">An assembly is the primary building block of a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span> <span data-ttu-id="0fcee-117">它是功能，可建置、 版本控制，以及部署為包含一或多個檔案的單一實作單元的集合。</span><span class="sxs-lookup"><span data-stu-id="0fcee-117">It is a collection of functionality that is built, versioned, and deployed as a single implementation unit containing one or more files.</span></span> <span data-ttu-id="0fcee-118">每個組件包含組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="0fcee-118">Each assembly contains an assembly manifest.</span></span>  
  
## <a name="type-libraries-and-assembly-manifests"></a><span data-ttu-id="0fcee-119">型別程式庫和組件資訊清單</span><span class="sxs-lookup"><span data-stu-id="0fcee-119">Type Libraries and Assembly Manifests</span></span>  
 <span data-ttu-id="0fcee-120">型別程式庫描述 COM 物件，例如成員名稱和資料類型的特性。</span><span class="sxs-lookup"><span data-stu-id="0fcee-120">Type libraries describe characteristics of COM objects, such as member names and data types.</span></span> <span data-ttu-id="0fcee-121">組件資訊清單執行相同的功能，如[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fcee-121">Assembly manifests perform the same function for [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications.</span></span> <span data-ttu-id="0fcee-122">包括下列資訊︰</span><span class="sxs-lookup"><span data-stu-id="0fcee-122">They include information about the following:</span></span>  
  
-   <span data-ttu-id="0fcee-123">組件識別、 版本、 文化特性和數位簽章。</span><span class="sxs-lookup"><span data-stu-id="0fcee-123">Assembly identity, version, culture, and digital signature.</span></span>  
  
-   <span data-ttu-id="0fcee-124">構成組件實作的檔案。</span><span class="sxs-lookup"><span data-stu-id="0fcee-124">Files that make up the assembly implementation.</span></span>  
  
-   <span data-ttu-id="0fcee-125">型別和構成組件的資源。</span><span class="sxs-lookup"><span data-stu-id="0fcee-125">Types and resources that make up the assembly.</span></span> <span data-ttu-id="0fcee-126">這包括從其匯出。</span><span class="sxs-lookup"><span data-stu-id="0fcee-126">This includes those that are exported from it.</span></span>  
  
-   <span data-ttu-id="0fcee-127">對其他組件的編譯時間相依性。</span><span class="sxs-lookup"><span data-stu-id="0fcee-127">Compile-time dependencies on other assemblies.</span></span>  
  
-   <span data-ttu-id="0fcee-128">組件正確執行所需的權限。</span><span class="sxs-lookup"><span data-stu-id="0fcee-128">Permissions required for the assembly to run correctly.</span></span>  
  
 <span data-ttu-id="0fcee-129">如需組件和組件資訊清單的詳細資訊，請參閱[組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0fcee-129">For more information about assemblies and assembly manifests, see [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
### <a name="importing-and-exporting-type-libraries"></a><span data-ttu-id="0fcee-130">匯入和匯出類型程式庫</span><span class="sxs-lookup"><span data-stu-id="0fcee-130">Importing and Exporting Type Libraries</span></span>  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="0fcee-131">包含公用程式，可讓您從類型程式庫匯入資訊的 Tlbimp[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fcee-131"> contains a utility, Tlbimp, that lets you import information from a type library into a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span> <span data-ttu-id="0fcee-132">您可以使用 Tlbexp 公用程式，從組件產生型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="0fcee-132">You can generate type libraries from assemblies by using the Tlbexp utility.</span></span>  
  
 <span data-ttu-id="0fcee-133">Tlbimp 和 Tlbexp 的相關資訊，請參閱[Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)和[Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)。</span><span class="sxs-lookup"><span data-stu-id="0fcee-133">For information about Tlbimp and Tlbexp, see [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) and [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="0fcee-134">Interop 組件</span><span class="sxs-lookup"><span data-stu-id="0fcee-134">Interop Assemblies</span></span>  
 <span data-ttu-id="0fcee-135">Interop 組件是[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件的橋接器之間 managed 和 unmanaged 程式碼，為對等用法的對應 COM 物件成員[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]管理成員。</span><span class="sxs-lookup"><span data-stu-id="0fcee-135">Interop assemblies are [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies that bridge between managed and unmanaged code, mapping COM object members to equivalent [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] managed members.</span></span> <span data-ttu-id="0fcee-136">所建立的 interop 組件[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]處理許多使用 COM 物件，例如交互操作性封送處理的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0fcee-136">Interop assemblies created by [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] handle many of the details of working with COM objects, such as interoperability marshaling.</span></span>  
  
## <a name="interoperability-marshaling"></a><span data-ttu-id="0fcee-137">互通性封送處理</span><span class="sxs-lookup"><span data-stu-id="0fcee-137">Interoperability Marshaling</span></span>  
 <span data-ttu-id="0fcee-138">所有[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式都共用一組啟用物件，不論所使用的程式設計語言的互通性的一般型別。</span><span class="sxs-lookup"><span data-stu-id="0fcee-138">All [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications share a set of common types that enable interoperability of objects, regardless of the programming language that is used.</span></span> <span data-ttu-id="0fcee-139">參數和傳回值的 COM 物件有時候會使用 managed 程式碼中使用的不同資料類型。</span><span class="sxs-lookup"><span data-stu-id="0fcee-139">The parameters and return values of COM objects sometimes use data types that differ from those used in managed code.</span></span> <span data-ttu-id="0fcee-140">*互通性封送處理*移動的 COM 物件會封裝參數和傳回值，為對等資料類型的程序。</span><span class="sxs-lookup"><span data-stu-id="0fcee-140">*Interoperability marshaling* is the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="0fcee-141">如需詳細資訊，請參閱[Interop 封送處理](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)。</span><span class="sxs-lookup"><span data-stu-id="0fcee-141">For more information, see [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcee-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fcee-142">See Also</span></span>  
 <span data-ttu-id="0fcee-143">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="0fcee-143">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="0fcee-144"> [逐步解說︰ 實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="0fcee-144"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="0fcee-145"> [與 Unmanaged 程式碼互通](https://msdn.microsoft.com/library/sd10k43k) </span><span class="sxs-lookup"><span data-stu-id="0fcee-145"> [Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/sd10k43k) </span></span>  
<span data-ttu-id="0fcee-146"> [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span><span class="sxs-lookup"><span data-stu-id="0fcee-146"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span></span>  
<span data-ttu-id="0fcee-147"> [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="0fcee-147"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="0fcee-148"> [Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span><span class="sxs-lookup"><span data-stu-id="0fcee-148"> [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span></span>  
<span data-ttu-id="0fcee-149"> [Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span><span class="sxs-lookup"><span data-stu-id="0fcee-149"> [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span></span>  
<span data-ttu-id="0fcee-150"> [Interop 封送處理](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a) </span><span class="sxs-lookup"><span data-stu-id="0fcee-150"> [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a) </span></span>  
<span data-ttu-id="0fcee-151"> [免註冊 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)</span><span class="sxs-lookup"><span data-stu-id="0fcee-151"> [Registration-Free COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)</span></span>
