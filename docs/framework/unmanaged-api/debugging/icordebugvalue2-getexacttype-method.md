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
ms.openlocfilehash: cb5bec66ab02de248109d8aaf444a93e67c2c6d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720356"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="943d9-102">ICorDebugValue2::GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="943d9-102">ICorDebugValue2::GetExactType Method</span></span>

<span data-ttu-id="943d9-103">取得 "ICorDebugType" 物件的介面指標，該物件代表 <xref:System.Type> 此值的。</span><span class="sxs-lookup"><span data-stu-id="943d9-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="943d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="943d9-105">參數</span><span class="sxs-lookup"><span data-stu-id="943d9-105">Parameters</span></span>  

 `ppType`  
 <span data-ttu-id="943d9-106">擴展物件位址的指標 `ICorDebugType` ，該物件表示 <xref:System.Type> 這個 "ICorDebugValue2" 物件所表示之值的。</span><span class="sxs-lookup"><span data-stu-id="943d9-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943d9-107">備註</span><span class="sxs-lookup"><span data-stu-id="943d9-107">Remarks</span></span>  

 <span data-ttu-id="943d9-108">泛型感知的 `GetExactType` 方法會取代 [ICorDebugObjectValue：： GetClass](icordebugobjectvalue-getclass-method.md) 和 [ICorDebugValue：： GetType](icordebugvalue-gettype-method.md) 方法，每個方法都會傳回值型別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="943d9-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="943d9-109">需求</span><span class="sxs-lookup"><span data-stu-id="943d9-109">Requirements</span></span>  

 <span data-ttu-id="943d9-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="943d9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="943d9-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="943d9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="943d9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="943d9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="943d9-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="943d9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943d9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="943d9-114">See also</span></span>
