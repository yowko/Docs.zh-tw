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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4d2ba850ffc6e49cf330174dda9524c7bac4549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709191"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="e6394-102">ICorDebugValue::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="e6394-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="e6394-103">取得這個 「 ICorDebugValue"物件的基本類型。</span><span class="sxs-lookup"><span data-stu-id="e6394-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6394-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6394-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6394-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6394-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="e6394-106">[out]值為"CorElementType"列舉，指出值的類型指標。</span><span class="sxs-lookup"><span data-stu-id="e6394-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6394-107">備註</span><span class="sxs-lookup"><span data-stu-id="e6394-107">Remarks</span></span>  
 <span data-ttu-id="e6394-108">如果物件是複雜的執行階段型別，該類型會檢查透過適當的子`ICorDebugValue`介面。</span><span class="sxs-lookup"><span data-stu-id="e6394-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="e6394-109">例如，"ICorDebugObjectValue 」，繼承自`ICorDebugValue`，表示複雜型別。</span><span class="sxs-lookup"><span data-stu-id="e6394-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="e6394-110">`GetType`並[icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)方法都會傳回值的型別資訊。</span><span class="sxs-lookup"><span data-stu-id="e6394-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="e6394-111">它們兩者都由取代感知泛型[ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e6394-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6394-112">需求</span><span class="sxs-lookup"><span data-stu-id="e6394-112">Requirements</span></span>  
 <span data-ttu-id="e6394-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6394-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6394-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6394-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6394-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6394-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6394-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6394-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6394-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6394-117">See also</span></span>

