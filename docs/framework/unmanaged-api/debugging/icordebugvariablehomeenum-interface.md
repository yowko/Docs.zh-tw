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
ms.openlocfilehash: d5962de8cc2762f6ecf4864c5255da0fe83918e4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396524"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="f5485-102">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f5485-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="f5485-103">提供函式中區域變數和引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f5485-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5485-104">方法</span><span class="sxs-lookup"><span data-stu-id="f5485-104">Methods</span></span>  
  
|<span data-ttu-id="f5485-105">方法</span><span class="sxs-lookup"><span data-stu-id="f5485-105">Method</span></span>|<span data-ttu-id="f5485-106">描述</span><span class="sxs-lookup"><span data-stu-id="f5485-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5485-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="f5485-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="f5485-108">取得指定的[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例數目，其中包含函式中區域變數和引數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f5485-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5485-109">備註</span><span class="sxs-lookup"><span data-stu-id="f5485-109">Remarks</span></span>  
 <span data-ttu-id="f5485-110">介面會實 `ICorDebugVariableHomeEnum` ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="f5485-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f5485-111">`ICorDebugVariableHomeEnum`實例會藉由呼叫[ICorDebugCode4：： EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md)方法來填入[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="f5485-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="f5485-112">集合中的每個[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例都代表函式中的區域變數或引數。</span><span class="sxs-lookup"><span data-stu-id="f5485-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="f5485-113">您可以藉由呼叫[ICorDebugVariableHomeEnum：： Next](icordebugvariablehomeenum-next-method.md)方法來列舉集合中的[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="f5485-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5485-114">需求</span><span class="sxs-lookup"><span data-stu-id="f5485-114">Requirements</span></span>  
 <span data-ttu-id="f5485-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5485-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5485-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5485-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5485-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5485-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5485-118">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5485-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5485-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f5485-119">See also</span></span>

- [<span data-ttu-id="f5485-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="f5485-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="f5485-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f5485-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
