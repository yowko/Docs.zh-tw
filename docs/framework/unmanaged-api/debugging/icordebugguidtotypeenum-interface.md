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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025820"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="64fe3-102">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="64fe3-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="64fe3-103">提供列舉值會定義一組的 Guid 和其對應的類型，都由 ICorDebugType 的執行個體之間的對應。</span><span class="sxs-lookup"><span data-stu-id="64fe3-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="64fe3-104">此介面繼承自 ICorDebugEnum 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="64fe3-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64fe3-105">方法</span><span class="sxs-lookup"><span data-stu-id="64fe3-105">Methods</span></span>  
  
|<span data-ttu-id="64fe3-106">方法</span><span class="sxs-lookup"><span data-stu-id="64fe3-106">Method</span></span>|<span data-ttu-id="64fe3-107">描述</span><span class="sxs-lookup"><span data-stu-id="64fe3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64fe3-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="64fe3-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="64fe3-109">取得指定的數目[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應 Guid 型別資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="64fe3-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64fe3-110">備註</span><span class="sxs-lookup"><span data-stu-id="64fe3-110">Remarks</span></span>  
 <span data-ttu-id="64fe3-111">`ICorDebugGuidToTypeEnum`介面物件可以藉由呼叫擷取[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="64fe3-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="64fe3-112">偵錯工具可以呼叫此介面[下一步](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)方法來擷取[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)中載入的物件表示受管理的 Windows 執行階段類型的表示法的對應用於呼叫的應用程式定義域[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="64fe3-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64fe3-113">需求</span><span class="sxs-lookup"><span data-stu-id="64fe3-113">Requirements</span></span>  
 <span data-ttu-id="64fe3-114">**平台：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="64fe3-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="64fe3-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64fe3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64fe3-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64fe3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64fe3-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64fe3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fe3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64fe3-118">See also</span></span>

- [<span data-ttu-id="64fe3-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="64fe3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
