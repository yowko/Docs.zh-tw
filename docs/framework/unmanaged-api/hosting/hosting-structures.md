---
title: 裝載結構
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
ms.openlocfilehash: 3d43225574b8794733ee2e83562699276ddc5bab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126930"
---
# <a name="hosting-structures"></a><span data-ttu-id="2be9a-102">裝載結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-102">Hosting Structures</span></span>
<span data-ttu-id="2be9a-103">本節說明裝載 API 所使用的非受控結構。</span><span class="sxs-lookup"><span data-stu-id="2be9a-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2be9a-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2be9a-104">In This Section</span></span>  
 [<span data-ttu-id="2be9a-105">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="2be9a-106">提供有關所參考元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2be9a-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="2be9a-107">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="2be9a-108">儲存事件的型別名稱，以及與事件相關聯的目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="2be9a-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="2be9a-109">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="2be9a-110">提供有關 common language runtime （CLR）之垃圾收集機制的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be9a-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="2be9a-111">COR_GC_THREAD_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="2be9a-112">包含有關垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be9a-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="2be9a-113">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="2be9a-114">描述要在錯誤報表中新增至自訂傾印的專案。</span><span class="sxs-lookup"><span data-stu-id="2be9a-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="2be9a-115">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="2be9a-116">提供 `Event_MDAFired` 事件的詳細資料，這會觸發建立 managed 偵錯工具（MDA）。</span><span class="sxs-lookup"><span data-stu-id="2be9a-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="2be9a-117">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="2be9a-118">提供參考模組和包含它之元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2be9a-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="2be9a-119">StackOverflowInfo 結構</span><span class="sxs-lookup"><span data-stu-id="2be9a-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="2be9a-120">儲存發生的溢位類型，以及因溢位而擲回之例外狀況的資訊。</span><span class="sxs-lookup"><span data-stu-id="2be9a-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2be9a-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="2be9a-121">Related Sections</span></span>  
 [<span data-ttu-id="2be9a-122">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="2be9a-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="2be9a-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="2be9a-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="2be9a-124">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2be9a-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="2be9a-125">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="2be9a-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
