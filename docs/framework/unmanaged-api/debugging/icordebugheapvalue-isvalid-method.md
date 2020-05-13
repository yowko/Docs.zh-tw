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
ms.openlocfilehash: e774905939640d2748344ad3f6e12a96f9868d9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213799"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="f2eca-102">ICorDebugHeapValue::IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="f2eca-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="f2eca-103">取得值，指出此 ICorDebugHeapValue 所表示的物件是否有效。</span><span class="sxs-lookup"><span data-stu-id="f2eca-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="f2eca-104">這個方法已在 .NET Framework 版本2.0 中被取代。</span><span class="sxs-lookup"><span data-stu-id="f2eca-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2eca-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2eca-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2eca-106">參數</span><span class="sxs-lookup"><span data-stu-id="f2eca-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="f2eca-107">脫銷布林值的指標，指出堆積上的這個值是否有效。</span><span class="sxs-lookup"><span data-stu-id="f2eca-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2eca-108">備註</span><span class="sxs-lookup"><span data-stu-id="f2eca-108">Remarks</span></span>  
 <span data-ttu-id="f2eca-109">如果垃圾收集行程已回收值，則該值無效。</span><span class="sxs-lookup"><span data-stu-id="f2eca-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="f2eca-110">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="f2eca-110">This method has been deprecated.</span></span> <span data-ttu-id="f2eca-111">在 .NET Framework 2.0 中，所有值都是有效的，直到呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)為止，此時值會無效。</span><span class="sxs-lookup"><span data-stu-id="f2eca-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2eca-112">需求</span><span class="sxs-lookup"><span data-stu-id="f2eca-112">Requirements</span></span>  
 <span data-ttu-id="f2eca-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2eca-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2eca-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2eca-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2eca-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2eca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2eca-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2eca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
