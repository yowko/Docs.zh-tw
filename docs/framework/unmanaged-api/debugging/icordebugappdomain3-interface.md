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
ms.openlocfilehash: 7c141ca9a8e1c74015883f45cb2eaa9183bb3d89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177524"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="718a1-102">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="718a1-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="718a1-103">提供方法來擷取資訊的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]目前已載入應用程式定義域中的類型。</span><span class="sxs-lookup"><span data-stu-id="718a1-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="718a1-104">這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="718a1-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="718a1-105">方法</span><span class="sxs-lookup"><span data-stu-id="718a1-105">Methods</span></span>  
  
|<span data-ttu-id="718a1-106">方法</span><span class="sxs-lookup"><span data-stu-id="718a1-106">Method</span></span>|<span data-ttu-id="718a1-107">描述</span><span class="sxs-lookup"><span data-stu-id="718a1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="718a1-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="718a1-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="718a1-109">取得列舉值，所有快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="718a1-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="718a1-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="718a1-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="718a1-111">取得列舉值的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]其介面識別項為基礎的應用程式定義域中的類型。</span><span class="sxs-lookup"><span data-stu-id="718a1-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="718a1-112">備註</span><span class="sxs-lookup"><span data-stu-id="718a1-112">Remarks</span></span>  
 <span data-ttu-id="718a1-113">這個介面適用於偵錯工具的函式評估呼叫搭配`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`。</span><span class="sxs-lookup"><span data-stu-id="718a1-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="718a1-114">當方法會擷取支援的介面識別項[!INCLUDE[wrt](../../../../includes/wrt-md.md)]伺服器物件，偵錯工具可以使用此介面中定義的方法，將其對應到對應至這些介面的 managed 型別。</span><span class="sxs-lookup"><span data-stu-id="718a1-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="718a1-115">若要擷取此介面的執行個體，請執行`QueryInterface`ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="718a1-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="718a1-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="718a1-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="718a1-117">需求</span><span class="sxs-lookup"><span data-stu-id="718a1-117">Requirements</span></span>  
 **<span data-ttu-id="718a1-118">平台：</span><span class="sxs-lookup"><span data-stu-id="718a1-118">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="718a1-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="718a1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="718a1-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="718a1-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="718a1-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="718a1-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="718a1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="718a1-122">See also</span></span>

- [<span data-ttu-id="718a1-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="718a1-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
