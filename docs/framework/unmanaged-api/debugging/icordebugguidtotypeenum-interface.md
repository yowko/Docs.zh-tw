---
title: "ICorDebugGuidToTypeEnum 介面"
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
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9993a5aaaef3d5b83d21e3641029af12119188da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="a88cc-102">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a88cc-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="a88cc-103">提供列舉值會定義 Guid，以及其對應的類型，都由 ICorDebugType 執行個體之間的對應。</span><span class="sxs-lookup"><span data-stu-id="a88cc-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="a88cc-104">此介面繼承自 ICorDebugEnum 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="a88cc-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a88cc-105">方法</span><span class="sxs-lookup"><span data-stu-id="a88cc-105">Methods</span></span>  
  
|<span data-ttu-id="a88cc-106">方法</span><span class="sxs-lookup"><span data-stu-id="a88cc-106">Method</span></span>|<span data-ttu-id="a88cc-107">描述</span><span class="sxs-lookup"><span data-stu-id="a88cc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a88cc-108">Icordebugguidtotypeenum:: Next</span><span class="sxs-lookup"><span data-stu-id="a88cc-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="a88cc-109">取得指定的數目[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應輸入資訊的 Guid 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a88cc-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a88cc-110">備註</span><span class="sxs-lookup"><span data-stu-id="a88cc-110">Remarks</span></span>  
 <span data-ttu-id="a88cc-111">`ICorDebugGuidToTypeEnum`介面物件可以藉由呼叫擷取[icordebugappdomain3:: Getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a88cc-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="a88cc-112">偵錯工具可以呼叫這個介面[下一步](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)方法來擷取[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)物件，表示對應的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]中載入的型別用於呼叫的應用程式定義域[icordebugappdomain3:: Getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a88cc-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a88cc-113">需求</span><span class="sxs-lookup"><span data-stu-id="a88cc-113">Requirements</span></span>  
 <span data-ttu-id="a88cc-114">**平台：**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a88cc-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="a88cc-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a88cc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a88cc-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a88cc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a88cc-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a88cc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88cc-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="a88cc-118">See Also</span></span>  
 [<span data-ttu-id="a88cc-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a88cc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
