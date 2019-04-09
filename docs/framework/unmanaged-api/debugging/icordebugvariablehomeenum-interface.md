---
title: ICorDebugVariableHomeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e67e4685320f56a4a6a8be2e3eb2e6c8065ce59
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080380"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="b84fd-102">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b84fd-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="b84fd-103">提供的本機變數和引數的函式中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b84fd-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b84fd-104">方法</span><span class="sxs-lookup"><span data-stu-id="b84fd-104">Methods</span></span>  
  
|<span data-ttu-id="b84fd-105">方法</span><span class="sxs-lookup"><span data-stu-id="b84fd-105">Method</span></span>|<span data-ttu-id="b84fd-106">描述</span><span class="sxs-lookup"><span data-stu-id="b84fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b84fd-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="b84fd-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="b84fd-108">取得指定的數目[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)包含區域變數和函式中的引數的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b84fd-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b84fd-109">備註</span><span class="sxs-lookup"><span data-stu-id="b84fd-109">Remarks</span></span>  
 <span data-ttu-id="b84fd-110">`ICorDebugVariableHomeEnum` ICorDebugEnum 介面實作的介面。</span><span class="sxs-lookup"><span data-stu-id="b84fd-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="b84fd-111">`ICorDebugVariableHomeEnum`執行個體填入[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)藉由呼叫的執行個體[ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b84fd-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="b84fd-112">每個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)集合中的執行個體代表的本機變數或函式中的引數。</span><span class="sxs-lookup"><span data-stu-id="b84fd-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="b84fd-113">[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)集合中的物件可以藉由呼叫列舉[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b84fd-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b84fd-114">需求</span><span class="sxs-lookup"><span data-stu-id="b84fd-114">Requirements</span></span>  
 <span data-ttu-id="b84fd-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b84fd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b84fd-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b84fd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b84fd-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b84fd-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b84fd-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b84fd-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b84fd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b84fd-119">See also</span></span>

- [<span data-ttu-id="b84fd-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="b84fd-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="b84fd-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b84fd-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
