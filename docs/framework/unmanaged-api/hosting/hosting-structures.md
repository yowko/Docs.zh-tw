---
title: 裝載結構
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b12af8c3c3a2f834827ff14665050e07b31467
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434682"
---
# <a name="hosting-structures"></a><span data-ttu-id="f37a6-102">裝載結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-102">Hosting Structures</span></span>
<span data-ttu-id="f37a6-103">本章節描述裝載 API 所使用的 unmanaged 的結構。</span><span class="sxs-lookup"><span data-stu-id="f37a6-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f37a6-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="f37a6-104">In This Section</span></span>  
 [<span data-ttu-id="f37a6-105">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="f37a6-106">提供參考組件的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="f37a6-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="f37a6-107">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="f37a6-108">儲存目前與事件相關聯的例外狀況事件和參數的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f37a6-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="f37a6-109">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="f37a6-110">提供有關 common language runtime (CLR) 記憶體回收機制統計資料。</span><span class="sxs-lookup"><span data-stu-id="f37a6-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="f37a6-111">COR_GC_THREAD_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="f37a6-112">包含記憶體回收相關的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="f37a6-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="f37a6-113">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="f37a6-114">描述要加入至自訂的傾印在錯誤報告中的項目。</span><span class="sxs-lookup"><span data-stu-id="f37a6-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="f37a6-115">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="f37a6-116">提供有關的詳細資料`Event_MDAFired`事件，以觸發建立的 managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="f37a6-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="f37a6-117">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="f37a6-118">提供參考的模組和包含它的組件的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="f37a6-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="f37a6-119">StackOverflowInfo 結構</span><span class="sxs-lookup"><span data-stu-id="f37a6-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="f37a6-120">因為溢位而擲回的例外狀況會儲存發生溢位和資訊的類型。</span><span class="sxs-lookup"><span data-stu-id="f37a6-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f37a6-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="f37a6-121">Related Sections</span></span>  
 [<span data-ttu-id="f37a6-122">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="f37a6-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="f37a6-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f37a6-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="f37a6-124">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f37a6-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="f37a6-125">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="f37a6-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
