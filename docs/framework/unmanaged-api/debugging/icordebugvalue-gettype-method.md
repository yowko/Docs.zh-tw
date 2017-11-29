---
title: "ICorDebugValue::GetType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d214da529aed40d33bdf18530560e9cd7b00f60a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="cc139-102">ICorDebugValue::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="cc139-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="cc139-103">取得這個 「 ICorDebugValue 」 物件的基本類型。</span><span class="sxs-lookup"><span data-stu-id="cc139-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc139-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc139-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc139-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc139-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="cc139-106">[out]值為"CorElementType 」 列舉值，指出值的類型指標。</span><span class="sxs-lookup"><span data-stu-id="cc139-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc139-107">備註</span><span class="sxs-lookup"><span data-stu-id="cc139-107">Remarks</span></span>  
 <span data-ttu-id="cc139-108">如果物件是複雜的執行階段類型，該類型可以透過適當的子類別檢查`ICorDebugValue`介面。</span><span class="sxs-lookup"><span data-stu-id="cc139-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="cc139-109">例如，"ICorDebugObjectValue 」，以繼承自`ICorDebugValue`，表示複雜類型。</span><span class="sxs-lookup"><span data-stu-id="cc139-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="cc139-110">`GetType`和[icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)方法都會傳回值的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="cc139-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="cc139-111">它們會同時取代感知泛型[icordebugvalue2:: Getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="cc139-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc139-112">需求</span><span class="sxs-lookup"><span data-stu-id="cc139-112">Requirements</span></span>  
 <span data-ttu-id="cc139-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc139-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc139-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc139-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc139-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc139-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc139-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc139-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc139-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc139-117">See Also</span></span>  
 
