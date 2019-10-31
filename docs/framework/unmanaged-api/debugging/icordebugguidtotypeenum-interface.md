---
title: ICorDebugGuidToTypeEnum 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138536"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="86e87-102">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="86e87-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="86e87-103">提供的列舉值會定義一組 Guid 與其對應類型（由 ICorDebugType 實例表示）之間的對應。</span><span class="sxs-lookup"><span data-stu-id="86e87-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="86e87-104">這個介面會繼承 ICorDebugEnum 介面中的方法。</span><span class="sxs-lookup"><span data-stu-id="86e87-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86e87-105">方法</span><span class="sxs-lookup"><span data-stu-id="86e87-105">Methods</span></span>  
  
|<span data-ttu-id="86e87-106">方法</span><span class="sxs-lookup"><span data-stu-id="86e87-106">Method</span></span>|<span data-ttu-id="86e87-107">描述</span><span class="sxs-lookup"><span data-stu-id="86e87-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86e87-108">ICorDebugGuidToTypeEnum：： Next</span><span class="sxs-lookup"><span data-stu-id="86e87-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="86e87-109">取得將 Guid 對應至類型資訊的指定[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)實例數目。</span><span class="sxs-lookup"><span data-stu-id="86e87-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e87-110">備註</span><span class="sxs-lookup"><span data-stu-id="86e87-110">Remarks</span></span>  
 <span data-ttu-id="86e87-111">藉由呼叫[ICorDebugAppDomain3：： GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法，可以抓取 `ICorDebugGuidToTypeEnum` 介面物件。</span><span class="sxs-lookup"><span data-stu-id="86e87-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="86e87-112">偵錯工具可以呼叫這個介面的[下一個](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)方法，來抓取[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)物件，以代表在用於呼叫[之應用程式域中載入的 Windows 執行階段類型的 managed 標記法對應ICorDebugAppDomain3：： GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="86e87-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e87-113">需求</span><span class="sxs-lookup"><span data-stu-id="86e87-113">Requirements</span></span>  
 <span data-ttu-id="86e87-114">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="86e87-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="86e87-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86e87-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86e87-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86e87-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86e87-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e87-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e87-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="86e87-118">See also</span></span>

- [<span data-ttu-id="86e87-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="86e87-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
