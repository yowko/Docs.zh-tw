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
ms.openlocfilehash: 7def2bd2c0f3ab501fdb918a0e9a7ee154159b78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791147"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="06fd4-102">ICorDebugValue::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="06fd4-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="06fd4-103">取得這個 "ICorDebugValue" 物件的基本類型。</span><span class="sxs-lookup"><span data-stu-id="06fd4-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="06fd4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06fd4-105">參數</span><span class="sxs-lookup"><span data-stu-id="06fd4-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="06fd4-106">脫銷"CorElementType" 列舉值的指標，指出值的類型。</span><span class="sxs-lookup"><span data-stu-id="06fd4-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06fd4-107">備註</span><span class="sxs-lookup"><span data-stu-id="06fd4-107">Remarks</span></span>  
 <span data-ttu-id="06fd4-108">如果物件是複雜的執行時間類型，則可以透過 `ICorDebugValue` 介面的適當子類別來檢查該類型。</span><span class="sxs-lookup"><span data-stu-id="06fd4-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="06fd4-109">例如，"ICorDebugObjectValue" （繼承自 `ICorDebugValue`）代表複雜類型。</span><span class="sxs-lookup"><span data-stu-id="06fd4-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="06fd4-110">`GetType` 和[ICorDebugObjectValue：： GetClass](icordebugobjectvalue-getclass-method.md)方法都會傳回數值型別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="06fd4-110">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="06fd4-111">兩者都被泛型感知[ICorDebugValue2：： GetExactType](icordebugvalue2-getexacttype-method.md)方法所取代。</span><span class="sxs-lookup"><span data-stu-id="06fd4-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06fd4-112">需求</span><span class="sxs-lookup"><span data-stu-id="06fd4-112">Requirements</span></span>  
 <span data-ttu-id="06fd4-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06fd4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06fd4-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06fd4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06fd4-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06fd4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06fd4-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06fd4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fd4-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="06fd4-117">See also</span></span>
