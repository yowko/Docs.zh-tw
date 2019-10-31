---
title: ICorDebugValue2::GetExactType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: 441d225dadbbca09ab27c8ccd70debe32f4c12da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140263"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="cf95f-102">ICorDebugValue2::GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="cf95f-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="cf95f-103">取得代表此值 <xref:System.Type> 之 "ICorDebugType" 物件的介面指標。</span><span class="sxs-lookup"><span data-stu-id="cf95f-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf95f-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf95f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf95f-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf95f-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="cf95f-106">脫銷`ICorDebugType` 物件位址的指標，表示這個 "ICorDebugValue2" 物件所表示之值的 <xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="cf95f-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf95f-107">備註</span><span class="sxs-lookup"><span data-stu-id="cf95f-107">Remarks</span></span>  
 <span data-ttu-id="cf95f-108">泛型感知 `GetExactType` 方法會取代[ICorDebugObjectValue：： GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)和[ICorDebugValue：： GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)方法，其中每一個都會傳回數值型別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cf95f-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf95f-109">需求</span><span class="sxs-lookup"><span data-stu-id="cf95f-109">Requirements</span></span>  
 <span data-ttu-id="cf95f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf95f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf95f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf95f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf95f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf95f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf95f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf95f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf95f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf95f-114">See also</span></span>
