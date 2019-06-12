---
title: ICorDebugAppDomain3 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025889"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="1ff88-102">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="1ff88-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="1ff88-103">提供方法來擷取目前已載入應用程式定義域中的 Windows 執行階段類型的 managed 表示法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1ff88-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="1ff88-104">這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1ff88-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ff88-105">方法</span><span class="sxs-lookup"><span data-stu-id="1ff88-105">Methods</span></span>  
  
|<span data-ttu-id="1ff88-106">方法</span><span class="sxs-lookup"><span data-stu-id="1ff88-106">Method</span></span>|<span data-ttu-id="1ff88-107">描述</span><span class="sxs-lookup"><span data-stu-id="1ff88-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ff88-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="1ff88-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="1ff88-109">取得所有快取的 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1ff88-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="1ff88-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="1ff88-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="1ff88-111">取得其介面識別項為基礎的應用程式定義域中快取的 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1ff88-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff88-112">備註</span><span class="sxs-lookup"><span data-stu-id="1ff88-112">Remarks</span></span>  
 <span data-ttu-id="1ff88-113">這個介面適用於偵錯工具的函式評估呼叫搭配`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`。</span><span class="sxs-lookup"><span data-stu-id="1ff88-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="1ff88-114">方法會擷取支援的 Windows 執行階段伺服器物件的介面識別項，偵錯工具可以將其對應到對應至這些介面的 managed 類型中使用此介面中定義的方法。</span><span class="sxs-lookup"><span data-stu-id="1ff88-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="1ff88-115">若要擷取此介面的執行個體，請執行`QueryInterface`ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="1ff88-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ff88-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1ff88-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff88-117">需求</span><span class="sxs-lookup"><span data-stu-id="1ff88-117">Requirements</span></span>  
 <span data-ttu-id="1ff88-118">**平台：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="1ff88-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="1ff88-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ff88-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ff88-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ff88-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ff88-121">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff88-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff88-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ff88-122">See also</span></span>

- [<span data-ttu-id="1ff88-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1ff88-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
