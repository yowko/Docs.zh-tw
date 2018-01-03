---
title: ".NET Framework 應用程式中的 COM 互通性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c84143e22f33f572447c50e33559a52469b181a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="77079-102">.NET Framework 應用程式中的 COM 互通性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77079-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="77079-103">當您想要使用相同的應用程式中的 COM 物件和.NET Framework 物件時，您必須先解決物件存在於記憶體中的差異。</span><span class="sxs-lookup"><span data-stu-id="77079-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="77079-104">.NET Framework 物件位於 managed 記憶體中，控制由 common language runtime 的記憶體，而且可能會視需要移動由執行階段。</span><span class="sxs-lookup"><span data-stu-id="77079-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="77079-105">COM 物件位於 unmanaged 記憶體中，而且不應該將移到另一個記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="77079-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="77079-106">和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供工具來控制這些互動 managed 和 unmanaged 元件。</span><span class="sxs-lookup"><span data-stu-id="77079-106"> and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="77079-107">如需 managed 程式碼的詳細資訊，請參閱[Common Language Runtime](../../../standard/clr.md)。</span><span class="sxs-lookup"><span data-stu-id="77079-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="77079-108">除了.NET 應用程式中使用之 COM 物件，您可能也想要使用[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]開發可從 unmanaged 程式碼，透過 COM 物件</span><span class="sxs-lookup"><span data-stu-id="77079-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="77079-109">在此頁面上的連結提供 COM 和.NET Framework 物件之間的互動的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="77079-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="77079-110">相關章節</span><span class="sxs-lookup"><span data-stu-id="77079-110">Related Sections</span></span>  
 [<span data-ttu-id="77079-111">COM Interop</span><span class="sxs-lookup"><span data-stu-id="77079-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="77079-112">提供包含在 Visual Basic 中，包括 COM 物件、 ActiveX 控制項、 Win32 Dll，受管理的物件，以及繼承的 COM 物件的 COM 互通性主題的連結。</span><span class="sxs-lookup"><span data-stu-id="77079-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="77079-113">COM Interop 包裝函式錯誤</span><span class="sxs-lookup"><span data-stu-id="77079-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="77079-114">描述如果專案系統無法建立特定元件的 COM 互通性包裝函式的結果和選項。</span><span class="sxs-lookup"><span data-stu-id="77079-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="77079-115">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="77079-115">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="77079-116">簡要說明 managed 和 unmanaged 程式碼之間的互動問題，並提供進一步的研究的連結。</span><span class="sxs-lookup"><span data-stu-id="77079-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="77079-117">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="77079-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="77079-118">討論執行階段可呼叫包裝函式，可讓 managed 程式碼呼叫 COM 方法，以及 COM 可呼叫包裝函式，可讓 COM 用戶端呼叫.NET 物件方法。</span><span class="sxs-lookup"><span data-stu-id="77079-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="77079-119">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="77079-119">Advanced COM Interoperability</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="77079-120">提供包含相對於包裝函式、 例外狀況、 繼承、 執行緒、 事件、 轉換、 轉換和封送處理的 COM 互通性主題的連結。</span><span class="sxs-lookup"><span data-stu-id="77079-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="77079-121">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="77079-121">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 <span data-ttu-id="77079-122">討論可用來將轉換為通用語言執行階段組件中的等效定義 COM 類型程式庫中找到的類型定義的工具。</span><span class="sxs-lookup"><span data-stu-id="77079-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
