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
ms.openlocfilehash: 1a02190b595fb01bdc2df46182bfa64bfe638db4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791281"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="438e5-102">ICorDebugType::GetFirstTypeParameter 方法</span><span class="sxs-lookup"><span data-stu-id="438e5-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="438e5-103">取得 ICorDebugType 的介面指標，表示此 `ICorDebugType`所表示之類型的第一個 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="438e5-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="438e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="438e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="438e5-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="438e5-106">脫銷表示第一個參數之 `ICorDebugType` 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="438e5-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="438e5-107">備註</span><span class="sxs-lookup"><span data-stu-id="438e5-107">Remarks</span></span>  
 <span data-ttu-id="438e5-108">當類型的其他資訊包含最多一個型別參數時，可以呼叫 `GetFirstTypeParameter`。</span><span class="sxs-lookup"><span data-stu-id="438e5-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="438e5-109">特別是，如果類型是 ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR （如[ICorDebugType：： GetType](icordebugtype-gettype-method.md)方法所示），就可以使用它。</span><span class="sxs-lookup"><span data-stu-id="438e5-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="438e5-110">需求</span><span class="sxs-lookup"><span data-stu-id="438e5-110">Requirements</span></span>  
 <span data-ttu-id="438e5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="438e5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="438e5-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="438e5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="438e5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="438e5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="438e5-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="438e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
