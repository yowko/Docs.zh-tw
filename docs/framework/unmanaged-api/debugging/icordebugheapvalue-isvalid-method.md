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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e1edb1d25a62a9a689c397339740e563d986c8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700214"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="15435-102">ICorDebugHeapValue::IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="15435-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="15435-103">取得值，指出此 ICorDebugHeapValue 所代表的物件是否有效。</span><span class="sxs-lookup"><span data-stu-id="15435-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="15435-104">這個方法已被取代，在.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="15435-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15435-105">語法</span><span class="sxs-lookup"><span data-stu-id="15435-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15435-106">參數</span><span class="sxs-lookup"><span data-stu-id="15435-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="15435-107">[out]布林值，指出是否在堆積上的這個值是有效的指標。</span><span class="sxs-lookup"><span data-stu-id="15435-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15435-108">備註</span><span class="sxs-lookup"><span data-stu-id="15435-108">Remarks</span></span>  
 <span data-ttu-id="15435-109">值不正確，如果它已經由記憶體回收行程回收。</span><span class="sxs-lookup"><span data-stu-id="15435-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="15435-110">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="15435-110">This method has been deprecated.</span></span> <span data-ttu-id="15435-111">在.NET Framework 2.0 中，所有值都是有效期限[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫時，在這段值都會失效。</span><span class="sxs-lookup"><span data-stu-id="15435-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15435-112">需求</span><span class="sxs-lookup"><span data-stu-id="15435-112">Requirements</span></span>  
 <span data-ttu-id="15435-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15435-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15435-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15435-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15435-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15435-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15435-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15435-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
