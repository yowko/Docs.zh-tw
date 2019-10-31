---
title: ICorDebugHeapValue::IsValid 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138405"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="f9c4a-102">ICorDebugHeapValue::IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="f9c4a-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="f9c4a-103">取得值，指出此 ICorDebugHeapValue 所表示的物件是否有效。</span><span class="sxs-lookup"><span data-stu-id="f9c4a-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="f9c4a-104">這個方法已在 .NET Framework 版本2.0 中被取代。</span><span class="sxs-lookup"><span data-stu-id="f9c4a-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c4a-105">語法</span><span class="sxs-lookup"><span data-stu-id="f9c4a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9c4a-106">參數</span><span class="sxs-lookup"><span data-stu-id="f9c4a-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="f9c4a-107">脫銷布林值的指標，指出堆積上的這個值是否有效。</span><span class="sxs-lookup"><span data-stu-id="f9c4a-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9c4a-108">備註</span><span class="sxs-lookup"><span data-stu-id="f9c4a-108">Remarks</span></span>  
 <span data-ttu-id="f9c4a-109">如果垃圾收集行程已回收值，則該值無效。</span><span class="sxs-lookup"><span data-stu-id="f9c4a-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="f9c4a-110">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="f9c4a-110">This method has been deprecated.</span></span> <span data-ttu-id="f9c4a-111">在 .NET Framework 2.0 中，所有值都是有效的，直到呼叫[ICorDebugController：： Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)為止，此時值會無效。</span><span class="sxs-lookup"><span data-stu-id="f9c4a-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c4a-112">需求</span><span class="sxs-lookup"><span data-stu-id="f9c4a-112">Requirements</span></span>  
 <span data-ttu-id="f9c4a-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c4a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9c4a-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9c4a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9c4a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9c4a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9c4a-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9c4a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
