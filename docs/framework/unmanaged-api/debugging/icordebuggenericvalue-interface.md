---
title: ICorDebugGenericValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 312b8b005998da44feb5ae24ab4a0a17bb948a3f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138563"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="cc173-102">ICorDebugGenericValue 介面</span><span class="sxs-lookup"><span data-stu-id="cc173-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="cc173-103">套用至所有值之 "ICorDebugValue" 的子類別。</span><span class="sxs-lookup"><span data-stu-id="cc173-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="cc173-104">這個介面提供值的 Get 和 Set 方法。</span><span class="sxs-lookup"><span data-stu-id="cc173-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc173-105">方法</span><span class="sxs-lookup"><span data-stu-id="cc173-105">Methods</span></span>  
  
|<span data-ttu-id="cc173-106">方法</span><span class="sxs-lookup"><span data-stu-id="cc173-106">Method</span></span>|<span data-ttu-id="cc173-107">描述</span><span class="sxs-lookup"><span data-stu-id="cc173-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc173-108">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="cc173-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="cc173-109">將值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cc173-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="cc173-110">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="cc173-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="cc173-111">從指定的緩衝區複製新的值。</span><span class="sxs-lookup"><span data-stu-id="cc173-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc173-112">備註</span><span class="sxs-lookup"><span data-stu-id="cc173-112">Remarks</span></span>  
 <span data-ttu-id="cc173-113">`ICorDebugGenericValue` 是子介面，因為它無法遠端處理。</span><span class="sxs-lookup"><span data-stu-id="cc173-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="cc173-114">對於參考型別，此值為參考，而不是參考的內容。</span><span class="sxs-lookup"><span data-stu-id="cc173-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="cc173-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="cc173-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc173-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="cc173-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc173-117">需求</span><span class="sxs-lookup"><span data-stu-id="cc173-117">Requirements</span></span>  
 <span data-ttu-id="cc173-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc173-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc173-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc173-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc173-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc173-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc173-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc173-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc173-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc173-122">See also</span></span>

- [<span data-ttu-id="cc173-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cc173-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
