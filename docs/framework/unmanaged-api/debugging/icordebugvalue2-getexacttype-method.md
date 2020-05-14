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
ms.openlocfilehash: dcec97bac2aefc8db1f9351f1dacb0f36fc0d2a0
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396802"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="c4c2e-102">ICorDebugValue2::GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="c4c2e-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="c4c2e-103">取得 "ICorDebugType" 物件的介面指標，表示 <xref:System.Type> 這個值的。</span><span class="sxs-lookup"><span data-stu-id="c4c2e-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4c2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4c2e-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4c2e-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="c4c2e-106">脫銷物件位址的指標 `ICorDebugType` ，代表 <xref:System.Type> 這個 "ICorDebugValue2" 物件所表示之值的。</span><span class="sxs-lookup"><span data-stu-id="c4c2e-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4c2e-107">備註</span><span class="sxs-lookup"><span data-stu-id="c4c2e-107">Remarks</span></span>  
 <span data-ttu-id="c4c2e-108">泛型感測方式會 `GetExactType` 同時取代[ICorDebugObjectValue：： GetClass](icordebugobjectvalue-getclass-method.md)和[ICorDebugValue：： GetType](icordebugvalue-gettype-method.md)方法，每個方法都會傳回數值型別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c4c2e-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c2e-109">需求</span><span class="sxs-lookup"><span data-stu-id="c4c2e-109">Requirements</span></span>  
 <span data-ttu-id="c4c2e-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c2e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c2e-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4c2e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4c2e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4c2e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4c2e-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c2e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c2e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c2e-114">See also</span></span>
