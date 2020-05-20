---
title: 裝載結構
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
ms.openlocfilehash: fb117352299a93aface6e58837307284ec4b8340
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616082"
---
# <a name="hosting-structures"></a><span data-ttu-id="53ab4-102">裝載結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-102">Hosting Structures</span></span>
<span data-ttu-id="53ab4-103">本節說明裝載 API 所使用的非受控結構。</span><span class="sxs-lookup"><span data-stu-id="53ab4-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53ab4-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="53ab4-104">In This Section</span></span>  
 [<span data-ttu-id="53ab4-105">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-105">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)  
 <span data-ttu-id="53ab4-106">提供有關所參考元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="53ab4-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="53ab4-107">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-107">BucketParameters Structure</span></span>](bucketparameters-structure.md)  
 <span data-ttu-id="53ab4-108">儲存事件的型別名稱，以及與事件相關聯的目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="53ab4-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="53ab4-109">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-109">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)  
 <span data-ttu-id="53ab4-110">提供有關 common language runtime （CLR）之垃圾收集機制的統計資料。</span><span class="sxs-lookup"><span data-stu-id="53ab4-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="53ab4-111">COR_GC_THREAD_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-111">COR_GC_THREAD_STATS Structure</span></span>](cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="53ab4-112">包含有關垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="53ab4-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="53ab4-113">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-113">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)  
 <span data-ttu-id="53ab4-114">描述要在錯誤報表中新增至自訂傾印的專案。</span><span class="sxs-lookup"><span data-stu-id="53ab4-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="53ab4-115">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-115">MDAInfo Structure</span></span>](mdainfo-structure.md)  
 <span data-ttu-id="53ab4-116">提供事件的相關詳細資料 `Event_MDAFired` ，這會觸發建立 managed 偵錯工具（MDA）。</span><span class="sxs-lookup"><span data-stu-id="53ab4-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="53ab4-117">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-117">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)  
 <span data-ttu-id="53ab4-118">提供參考模組和包含它之元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="53ab4-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="53ab4-119">StackOverflowInfo 結構</span><span class="sxs-lookup"><span data-stu-id="53ab4-119">StackOverflowInfo Structure</span></span>](stackoverflowinfo-structure.md)  
 <span data-ttu-id="53ab4-120">儲存發生的溢位類型，以及因溢位而擲回之例外狀況的資訊。</span><span class="sxs-lookup"><span data-stu-id="53ab4-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53ab4-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="53ab4-121">Related Sections</span></span>  
 [<span data-ttu-id="53ab4-122">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="53ab4-122">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="53ab4-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="53ab4-123">Hosting Interfaces</span></span>](hosting-interfaces.md)  
  
 [<span data-ttu-id="53ab4-124">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="53ab4-124">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="53ab4-125">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="53ab4-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
