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
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790939"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="e9eb2-102">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e9eb2-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="e9eb2-103">提供函式中區域變數和引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e9eb2-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9eb2-104">方法</span><span class="sxs-lookup"><span data-stu-id="e9eb2-104">Methods</span></span>  
  
|<span data-ttu-id="e9eb2-105">方法</span><span class="sxs-lookup"><span data-stu-id="e9eb2-105">Method</span></span>|<span data-ttu-id="e9eb2-106">描述</span><span class="sxs-lookup"><span data-stu-id="e9eb2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9eb2-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="e9eb2-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="e9eb2-108">取得指定的[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例數目，其中包含函式中區域變數和引數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e9eb2-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9eb2-109">備註</span><span class="sxs-lookup"><span data-stu-id="e9eb2-109">Remarks</span></span>  
 <span data-ttu-id="e9eb2-110">`ICorDebugVariableHomeEnum` 介面會執行 ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="e9eb2-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="e9eb2-111">`ICorDebugVariableHomeEnum` 實例會藉由呼叫[ICorDebugCode4：： EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md)方法來填入[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="e9eb2-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="e9eb2-112">集合中的每個[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例都代表函式中的區域變數或引數。</span><span class="sxs-lookup"><span data-stu-id="e9eb2-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="e9eb2-113">您可以藉由呼叫[ICorDebugVariableHomeEnum：： Next](icordebugvariablehomeenum-next-method.md)方法來列舉集合中的[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="e9eb2-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9eb2-114">需求</span><span class="sxs-lookup"><span data-stu-id="e9eb2-114">Requirements</span></span>  
 <span data-ttu-id="e9eb2-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9eb2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9eb2-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9eb2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9eb2-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9eb2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9eb2-118">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9eb2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9eb2-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9eb2-119">See also</span></span>

- [<span data-ttu-id="e9eb2-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="e9eb2-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="e9eb2-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e9eb2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
