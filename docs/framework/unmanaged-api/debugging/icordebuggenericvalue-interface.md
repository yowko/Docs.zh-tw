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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988672"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="f9f5d-102">ICorDebugGenericValue 介面</span><span class="sxs-lookup"><span data-stu-id="f9f5d-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="f9f5d-103">「 ICorDebugValue"，套用至所有值的子類別。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="f9f5d-104">這個介面提供值的 Get 和 Set 方法。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9f5d-105">方法</span><span class="sxs-lookup"><span data-stu-id="f9f5d-105">Methods</span></span>  
  
|<span data-ttu-id="f9f5d-106">方法</span><span class="sxs-lookup"><span data-stu-id="f9f5d-106">Method</span></span>|<span data-ttu-id="f9f5d-107">描述</span><span class="sxs-lookup"><span data-stu-id="f9f5d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9f5d-108">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="f9f5d-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="f9f5d-109">將值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="f9f5d-110">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="f9f5d-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="f9f5d-111">複製指定的緩衝區中的新值。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9f5d-112">備註</span><span class="sxs-lookup"><span data-stu-id="f9f5d-112">Remarks</span></span>  
 <span data-ttu-id="f9f5d-113">`ICorDebugGenericValue` 因為它是非可遠端處理，則是子介面。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="f9f5d-114">若是參考類型，值會是參考，而不是參考的內容。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="f9f5d-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9f5d-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9f5d-117">需求</span><span class="sxs-lookup"><span data-stu-id="f9f5d-117">Requirements</span></span>  
 <span data-ttu-id="f9f5d-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f9f5d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9f5d-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9f5d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9f5d-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9f5d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9f5d-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9f5d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f5d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9f5d-122">See also</span></span>

- [<span data-ttu-id="f9f5d-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f9f5d-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
