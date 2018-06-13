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
ms.openlocfilehash: 95532d6721467b482b1d79d611f8055b606bb4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413504"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="473b1-102">ICorDebugHeapValue::IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="473b1-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="473b1-103">取得值，指出此 ICorDebugHeapValue 所表示的物件是否有效。</span><span class="sxs-lookup"><span data-stu-id="473b1-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="473b1-104">.NET Framework 2.0 版中，這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="473b1-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="473b1-105">語法</span><span class="sxs-lookup"><span data-stu-id="473b1-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="473b1-106">參數</span><span class="sxs-lookup"><span data-stu-id="473b1-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="473b1-107">[out]布林值，指出是否在堆積上的這個值是有效的指標。</span><span class="sxs-lookup"><span data-stu-id="473b1-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="473b1-108">備註</span><span class="sxs-lookup"><span data-stu-id="473b1-108">Remarks</span></span>  
 <span data-ttu-id="473b1-109">值不正確，如果它已經由記憶體回收行程回收。</span><span class="sxs-lookup"><span data-stu-id="473b1-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="473b1-110">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="473b1-110">This method has been deprecated.</span></span> <span data-ttu-id="473b1-111">在.NET Framework 2.0 中，所有值都都有效，直到[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫時，在這段值都會失效。</span><span class="sxs-lookup"><span data-stu-id="473b1-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="473b1-112">需求</span><span class="sxs-lookup"><span data-stu-id="473b1-112">Requirements</span></span>  
 <span data-ttu-id="473b1-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="473b1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="473b1-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="473b1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="473b1-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="473b1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="473b1-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="473b1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
