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
ms.openlocfilehash: d9150d15ac183b65b87448424f265693ed7b7ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726570"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="79599-102">ICorDebugHeapValue::IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="79599-102">ICorDebugHeapValue::IsValid Method</span></span>

<span data-ttu-id="79599-103">取得值，這個值表示此 ICorDebugHeapValue 所表示的物件是否有效。</span><span class="sxs-lookup"><span data-stu-id="79599-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="79599-104">在 .NET Framework 版本2.0 中，此方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="79599-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79599-105">語法</span><span class="sxs-lookup"><span data-stu-id="79599-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79599-106">參數</span><span class="sxs-lookup"><span data-stu-id="79599-106">Parameters</span></span>  

 `pbValid`  
 <span data-ttu-id="79599-107">擴展布林值的指標，指出堆積上的此值是否有效。</span><span class="sxs-lookup"><span data-stu-id="79599-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79599-108">備註</span><span class="sxs-lookup"><span data-stu-id="79599-108">Remarks</span></span>  

 <span data-ttu-id="79599-109">如果它已經由垃圾收集行程回收，則該值無效。</span><span class="sxs-lookup"><span data-stu-id="79599-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="79599-110">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="79599-110">This method has been deprecated.</span></span> <span data-ttu-id="79599-111">在 .NET Framework 2.0 中，在呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 之前，所有值都是有效的，此時值會失效。</span><span class="sxs-lookup"><span data-stu-id="79599-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79599-112">需求</span><span class="sxs-lookup"><span data-stu-id="79599-112">Requirements</span></span>  

 <span data-ttu-id="79599-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79599-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79599-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79599-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79599-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79599-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79599-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79599-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
