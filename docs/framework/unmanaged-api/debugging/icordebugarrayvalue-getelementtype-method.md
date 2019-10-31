---
title: ICorDebugArrayValue::GetElementType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: d4de3405f84bfc08f7e1519bc7f9604eb1f5a14e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088296"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="89a3f-102">ICorDebugArrayValue::GetElementType 方法</span><span class="sxs-lookup"><span data-stu-id="89a3f-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="89a3f-103">取得值，指出陣列中元素的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="89a3f-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89a3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="89a3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89a3f-105">參數</span><span class="sxs-lookup"><span data-stu-id="89a3f-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="89a3f-106">脫銷指出類型之 CorElementType 列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="89a3f-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89a3f-107">需求</span><span class="sxs-lookup"><span data-stu-id="89a3f-107">Requirements</span></span>  
 <span data-ttu-id="89a3f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89a3f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89a3f-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89a3f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89a3f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89a3f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89a3f-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89a3f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
