---
title: ICorDebugObjectValue::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a20ab7a7ecb5d01351d0c912e08955f44b26d5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756993"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="4df7e-102">ICorDebugObjectValue::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="4df7e-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="4df7e-103">取得這個物件值的類別。</span><span class="sxs-lookup"><span data-stu-id="4df7e-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df7e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4df7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4df7e-105">參數</span><span class="sxs-lookup"><span data-stu-id="4df7e-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="4df7e-106">[out]表示物件值，這個 「 ICorDebugObjectValue 」 物件所表示的類別 「 ICorDebugClass"物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="4df7e-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4df7e-107">備註</span><span class="sxs-lookup"><span data-stu-id="4df7e-107">Remarks</span></span>  
 <span data-ttu-id="4df7e-108">`GetClass`並[icordebugvalue:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)方法都會傳回值的類型的相關資訊; 它們同時由取代感知泛型[ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="4df7e-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df7e-109">需求</span><span class="sxs-lookup"><span data-stu-id="4df7e-109">Requirements</span></span>  
 <span data-ttu-id="4df7e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4df7e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df7e-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4df7e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4df7e-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4df7e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4df7e-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df7e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df7e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4df7e-114">See also</span></span>
