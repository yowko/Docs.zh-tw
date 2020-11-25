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
ms.openlocfilehash: 149c5b09639c8809e736ade09566e7b1b530e3eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705705"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="894a8-102">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="894a8-102">ICorDebugGuidToTypeEnum Interface</span></span>

<span data-ttu-id="894a8-103">提供列舉值，這個列舉值會定義一組 Guid 與其對應類型之間的對應，這些類型是由 ICorDebugType 實例表示。</span><span class="sxs-lookup"><span data-stu-id="894a8-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="894a8-104">此介面繼承 ICorDebugEnum 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="894a8-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="894a8-105">方法</span><span class="sxs-lookup"><span data-stu-id="894a8-105">Methods</span></span>  
  
|<span data-ttu-id="894a8-106">方法</span><span class="sxs-lookup"><span data-stu-id="894a8-106">Method</span></span>|<span data-ttu-id="894a8-107">描述</span><span class="sxs-lookup"><span data-stu-id="894a8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="894a8-108">ICorDebugGuidToTypeEnum：： Next</span><span class="sxs-lookup"><span data-stu-id="894a8-108">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="894a8-109">取得將 Guid 對應至類型資訊的指定 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 實例數目。</span><span class="sxs-lookup"><span data-stu-id="894a8-109">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="894a8-110">備註</span><span class="sxs-lookup"><span data-stu-id="894a8-110">Remarks</span></span>  

 <span data-ttu-id="894a8-111">藉 `ICorDebugGuidToTypeEnum` 由呼叫 [ICorDebugAppDomain3：： GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) 方法，即可取出介面物件。</span><span class="sxs-lookup"><span data-stu-id="894a8-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="894a8-112">偵錯工具可以呼叫這個介面的 [Next](icordebugguidtotypeenum-next-method.md) 方法來取出 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 物件，這些物件代表載入至用來呼叫 [ICorDebugAppDomain3：： GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) 方法 Windows 執行階段之應用程式域中的 managed 標記法對應。</span><span class="sxs-lookup"><span data-stu-id="894a8-112">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="894a8-113">需求</span><span class="sxs-lookup"><span data-stu-id="894a8-113">Requirements</span></span>  

 <span data-ttu-id="894a8-114">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="894a8-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="894a8-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="894a8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="894a8-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="894a8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="894a8-117">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="894a8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894a8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="894a8-118">See also</span></span>

- [<span data-ttu-id="894a8-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="894a8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
