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
ms.openlocfilehash: 7c5359ddf2c021f77ad1ea0a8579316c3c773fd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209782"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="7170b-102">ICorDebugGenericValue 介面</span><span class="sxs-lookup"><span data-stu-id="7170b-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="7170b-103">套用至所有值之 "ICorDebugValue" 的子類別。</span><span class="sxs-lookup"><span data-stu-id="7170b-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="7170b-104">這個介面提供值的 Get 和 Set 方法。</span><span class="sxs-lookup"><span data-stu-id="7170b-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7170b-105">方法</span><span class="sxs-lookup"><span data-stu-id="7170b-105">Methods</span></span>  
  
|<span data-ttu-id="7170b-106">方法</span><span class="sxs-lookup"><span data-stu-id="7170b-106">Method</span></span>|<span data-ttu-id="7170b-107">描述</span><span class="sxs-lookup"><span data-stu-id="7170b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7170b-108">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="7170b-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="7170b-109">將值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7170b-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="7170b-110">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="7170b-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="7170b-111">從指定的緩衝區複製新的值。</span><span class="sxs-lookup"><span data-stu-id="7170b-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7170b-112">備註</span><span class="sxs-lookup"><span data-stu-id="7170b-112">Remarks</span></span>  
 <span data-ttu-id="7170b-113">`ICorDebugGenericValue`是子介面，因為它無法遠端處理。</span><span class="sxs-lookup"><span data-stu-id="7170b-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="7170b-114">對於參考型別，此值為參考，而不是參考的內容。</span><span class="sxs-lookup"><span data-stu-id="7170b-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="7170b-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7170b-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7170b-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7170b-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7170b-117">需求</span><span class="sxs-lookup"><span data-stu-id="7170b-117">Requirements</span></span>  
 <span data-ttu-id="7170b-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7170b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7170b-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7170b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7170b-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7170b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7170b-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7170b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7170b-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="7170b-122">See also</span></span>

- [<span data-ttu-id="7170b-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7170b-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
