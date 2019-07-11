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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c28ff84b08802246d587bfa130ae5915177932ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764300"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="79486-102">ICorDebugValue2::GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="79486-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="79486-103">若"ICorDebugType 」 物件，表示要取得的介面指標<xref:System.Type>此值。</span><span class="sxs-lookup"><span data-stu-id="79486-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79486-104">語法</span><span class="sxs-lookup"><span data-stu-id="79486-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79486-105">參數</span><span class="sxs-lookup"><span data-stu-id="79486-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="79486-106">[out]位址指標`ICorDebugType`物件，表示<xref:System.Type>的這個 「 ICorDebugValue2 」 物件所表示的值。</span><span class="sxs-lookup"><span data-stu-id="79486-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79486-107">備註</span><span class="sxs-lookup"><span data-stu-id="79486-107">Remarks</span></span>  
 <span data-ttu-id="79486-108">感知泛型`GetExactType`方法會取代兩者[icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)並[icordebugvalue:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)方法，每個傳回值的型別相關資訊.</span><span class="sxs-lookup"><span data-stu-id="79486-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79486-109">需求</span><span class="sxs-lookup"><span data-stu-id="79486-109">Requirements</span></span>  
 <span data-ttu-id="79486-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79486-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79486-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79486-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79486-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79486-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79486-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79486-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79486-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79486-114">See also</span></span>
