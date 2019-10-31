---
title: ICorDebugValue::GetType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 284a74823b01305f8c6e025f70bb9209c8607b7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137080"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="8b8a3-102">ICorDebugValue::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="8b8a3-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="8b8a3-103">取得這個 "ICorDebugValue" 物件的基本類型。</span><span class="sxs-lookup"><span data-stu-id="8b8a3-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b8a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b8a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b8a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b8a3-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="8b8a3-106">脫銷"CorElementType" 列舉值的指標，指出值的類型。</span><span class="sxs-lookup"><span data-stu-id="8b8a3-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b8a3-107">備註</span><span class="sxs-lookup"><span data-stu-id="8b8a3-107">Remarks</span></span>  
 <span data-ttu-id="8b8a3-108">如果物件是複雜的執行時間類型，則可以透過 `ICorDebugValue` 介面的適當子類別來檢查該類型。</span><span class="sxs-lookup"><span data-stu-id="8b8a3-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="8b8a3-109">例如，"ICorDebugObjectValue" （繼承自 `ICorDebugValue`）代表複雜類型。</span><span class="sxs-lookup"><span data-stu-id="8b8a3-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="8b8a3-110">`GetType` 和[ICorDebugObjectValue：： GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)方法都會傳回數值型別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8b8a3-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="8b8a3-111">兩者都被泛型感知[ICorDebugValue2：： GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)方法所取代。</span><span class="sxs-lookup"><span data-stu-id="8b8a3-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b8a3-112">需求</span><span class="sxs-lookup"><span data-stu-id="8b8a3-112">Requirements</span></span>  
 <span data-ttu-id="8b8a3-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b8a3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b8a3-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b8a3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b8a3-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b8a3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b8a3-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b8a3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8a3-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b8a3-117">See also</span></span>
