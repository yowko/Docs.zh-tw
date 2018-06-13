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
ms.openlocfilehash: a80a334d1b586aec30c6cf2715d7fb841bc76929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423256"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="64e1a-102">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="64e1a-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="64e1a-103">提供的本機變數和引數的函式中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="64e1a-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64e1a-104">方法</span><span class="sxs-lookup"><span data-stu-id="64e1a-104">Methods</span></span>  
  
|<span data-ttu-id="64e1a-105">方法</span><span class="sxs-lookup"><span data-stu-id="64e1a-105">Method</span></span>|<span data-ttu-id="64e1a-106">描述</span><span class="sxs-lookup"><span data-stu-id="64e1a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64e1a-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="64e1a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="64e1a-108">取得指定的數目[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)包含本機變數和引數的函式中的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="64e1a-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64e1a-109">備註</span><span class="sxs-lookup"><span data-stu-id="64e1a-109">Remarks</span></span>  
 <span data-ttu-id="64e1a-110">`ICorDebugVariableHomeEnum`介面會實作 ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="64e1a-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="64e1a-111">`ICorDebugVariableHomeEnum`執行個體填入[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)藉由呼叫的執行個體[ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="64e1a-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="64e1a-112">每個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)集合中的執行個體代表本機變數或引數的函式中。</span><span class="sxs-lookup"><span data-stu-id="64e1a-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="64e1a-113">[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)可列舉集合中的物件，藉由呼叫[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="64e1a-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e1a-114">需求</span><span class="sxs-lookup"><span data-stu-id="64e1a-114">Requirements</span></span>  
 <span data-ttu-id="64e1a-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64e1a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e1a-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64e1a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64e1a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64e1a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64e1a-118">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64e1a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e1a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64e1a-119">See Also</span></span>  
 [<span data-ttu-id="64e1a-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="64e1a-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="64e1a-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="64e1a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
