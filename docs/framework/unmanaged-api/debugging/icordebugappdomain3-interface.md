---
title: "ICorDebugAppDomain3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 017a2f018569b17c0b0011638e16f1921b6c9801
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="5d0ed-102">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="5d0ed-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="5d0ed-103">提供方法來擷取資訊的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]目前載入的應用程式定義域中的類型。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="5d0ed-104">這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d0ed-105">方法</span><span class="sxs-lookup"><span data-stu-id="5d0ed-105">Methods</span></span>  
  
|<span data-ttu-id="5d0ed-106">方法</span><span class="sxs-lookup"><span data-stu-id="5d0ed-106">Method</span></span>|<span data-ttu-id="5d0ed-107">描述</span><span class="sxs-lookup"><span data-stu-id="5d0ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d0ed-108">Icordebugappdomain3:: Getcachedwinrttypes</span><span class="sxs-lookup"><span data-stu-id="5d0ed-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="5d0ed-109">取得列舉值，所有快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="5d0ed-110">Icordebugappdomain3:: Getcachedwinrttypesforiids</span><span class="sxs-lookup"><span data-stu-id="5d0ed-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="5d0ed-111">取得列舉值的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]應用程式定義域中的類型取決於其介面識別項。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d0ed-112">備註</span><span class="sxs-lookup"><span data-stu-id="5d0ed-112">Remarks</span></span>  
 <span data-ttu-id="5d0ed-113">這個介面是用於偵錯工具的函式評估呼叫搭配`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="5d0ed-114">當方法會擷取所支援的介面識別碼[!INCLUDE[wrt](../../../../includes/wrt-md.md)]伺服器物件時，偵錯工具可能會使用此介面中定義的方法以對應至對應到這些介面的 managed 型別。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="5d0ed-115">若要擷取此介面的執行個體，執行`QueryInterface`ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d0ed-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5d0ed-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d0ed-117">需求</span><span class="sxs-lookup"><span data-stu-id="5d0ed-117">Requirements</span></span>  
 <span data-ttu-id="5d0ed-118">**平台：**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d0ed-118">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="5d0ed-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d0ed-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d0ed-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d0ed-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d0ed-121">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d0ed-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0ed-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d0ed-122">See Also</span></span>  
 [<span data-ttu-id="5d0ed-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5d0ed-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
