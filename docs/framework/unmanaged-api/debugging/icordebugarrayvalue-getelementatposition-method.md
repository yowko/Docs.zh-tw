---
title: ICorDebugArrayValue::GetElementAtPosition 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76100116f2ca3a9b9a99477ca2352d5fa1335ab2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502250"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="65fee-102">ICorDebugArrayValue::GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="65fee-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="65fee-103">取得陣列視為的以零為起始的一維陣列的指定位置的項目。</span><span class="sxs-lookup"><span data-stu-id="65fee-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65fee-104">語法</span><span class="sxs-lookup"><span data-stu-id="65fee-104">Syntax</span></span>  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65fee-105">參數</span><span class="sxs-lookup"><span data-stu-id="65fee-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="65fee-106">[in]要擷取之項目的位置。</span><span class="sxs-lookup"><span data-stu-id="65fee-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="65fee-107">[out]ICorDebugValue 物件，表示項目的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="65fee-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65fee-108">備註</span><span class="sxs-lookup"><span data-stu-id="65fee-108">Remarks</span></span>  
 <span data-ttu-id="65fee-109">多維度陣列的配置會遵循 c + + 樣式的陣列配置。</span><span class="sxs-lookup"><span data-stu-id="65fee-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65fee-110">需求</span><span class="sxs-lookup"><span data-stu-id="65fee-110">Requirements</span></span>  
 <span data-ttu-id="65fee-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65fee-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65fee-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65fee-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65fee-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65fee-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65fee-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65fee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
