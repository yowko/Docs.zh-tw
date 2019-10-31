---
title: ICorDebugType::GetFirstTypeParameter 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4dbc042143e68dc962eb21b2bf741cbaefc1977e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122349"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="d3da2-102">ICorDebugType::GetFirstTypeParameter 方法</span><span class="sxs-lookup"><span data-stu-id="d3da2-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="d3da2-103">取得 ICorDebugType 的介面指標，表示此 `ICorDebugType`所表示之類型的第一個 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="d3da2-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3da2-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3da2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3da2-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3da2-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="d3da2-106">脫銷表示第一個參數之 `ICorDebugType` 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d3da2-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3da2-107">備註</span><span class="sxs-lookup"><span data-stu-id="d3da2-107">Remarks</span></span>  
 <span data-ttu-id="d3da2-108">當類型的其他資訊包含最多一個型別參數時，可以呼叫 `GetFirstTypeParameter`。</span><span class="sxs-lookup"><span data-stu-id="d3da2-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="d3da2-109">特別是，如果類型是 ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR （如[ICorDebugType：： GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法所指示），則可以使用它。</span><span class="sxs-lookup"><span data-stu-id="d3da2-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3da2-110">需求</span><span class="sxs-lookup"><span data-stu-id="d3da2-110">Requirements</span></span>  
 <span data-ttu-id="d3da2-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3da2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3da2-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3da2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3da2-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3da2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3da2-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3da2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
