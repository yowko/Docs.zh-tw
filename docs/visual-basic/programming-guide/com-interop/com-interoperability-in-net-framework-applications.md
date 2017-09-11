---
title: ".NET Framework 應用程式 (Visual Basic) 中的 COM 互通性 |Microsoft 文件"
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
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
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
ms.openlocfilehash: 6b68f35c1c63e2d7d229f89336b86c4a062e5ec9
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="8f44f-102">.NET Framework 應用程式中的 COM 互通性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f44f-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="8f44f-103">當您想要在相同的應用程式中使用 COM 物件和.NET Framework 物件時，您需要處理的物件存在於記憶體中的差異。</span><span class="sxs-lookup"><span data-stu-id="8f44f-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="8f44f-104">在.NET Framework 物件位於 managed 記憶體 — common language runtime 所控制的記憶體，視需要可由執行階段移。</span><span class="sxs-lookup"><span data-stu-id="8f44f-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="8f44f-105">COM 物件位於 unmanaged 記憶體中，而且不應該將移至另一個記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="8f44f-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="8f44f-106">而[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]提供工具來控制這些互動 managed 和 unmanaged 元件。</span><span class="sxs-lookup"><span data-stu-id="8f44f-106"> and the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="8f44f-107">如需 managed 程式碼的詳細資訊，請參閱[Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)。</span><span class="sxs-lookup"><span data-stu-id="8f44f-107">For more information about managed code, see [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span></span>  
  
 <span data-ttu-id="8f44f-108">除了.NET 應用程式中使用 COM 物件，您可能也想要使用[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]來開發可從 unmanaged 程式碼，透過 COM 存取的物件</span><span class="sxs-lookup"><span data-stu-id="8f44f-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="8f44f-109">此頁面上的連結提供 COM 和.NET Framework 物件之間的互動的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8f44f-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8f44f-110">相關章節</span><span class="sxs-lookup"><span data-stu-id="8f44f-110">Related Sections</span></span>  
 [<span data-ttu-id="8f44f-111">COM Interop</span><span class="sxs-lookup"><span data-stu-id="8f44f-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="8f44f-112">提供連結，這些主題涵蓋在 Visual Basic 中，包括 COM 物件、 ActiveX 控制項、 Win32 Dll、 受管理的物件和 COM 物件的繼承的 COM 互通性。</span><span class="sxs-lookup"><span data-stu-id="8f44f-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="8f44f-113">COM Interop 包裝函式錯誤</span><span class="sxs-lookup"><span data-stu-id="8f44f-113">COM Interop Wrapper Error</span></span>](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="8f44f-114">專案系統無法建立特定元件的 COM 互通性包裝函式所描述的後果和選項。</span><span class="sxs-lookup"><span data-stu-id="8f44f-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="8f44f-115">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="8f44f-115">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="8f44f-116">簡短描述 managed 和 unmanaged 程式碼之間的互動問題，並提供連結，如需進一步的研究。</span><span class="sxs-lookup"><span data-stu-id="8f44f-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="8f44f-117">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="8f44f-117">COM Wrappers</span></span>](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 <span data-ttu-id="8f44f-118">討論執行階段可呼叫包裝函式，可讓 managed 程式碼呼叫 COM 方法，以及 COM 可呼叫包裝函式，可讓 COM 用戶端呼叫.NET 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="8f44f-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="8f44f-119">進階的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="8f44f-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="8f44f-120">提供連結，這些主題涵蓋與包裝函式、 例外狀況、 繼承、 執行緒、 事件、 轉換、 轉換和封送處理 COM 互通性。</span><span class="sxs-lookup"><span data-stu-id="8f44f-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="8f44f-121">Tlbimp.exe （類型程式庫匯入工具）</span><span class="sxs-lookup"><span data-stu-id="8f44f-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="8f44f-122">討論您可以使用轉換為通用語言執行階段組件中的等效定義 COM 類型程式庫中找到的類型定義的工具。</span><span class="sxs-lookup"><span data-stu-id="8f44f-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
