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
ms.openlocfilehash: 10584442d7e0bd61e6decaf2b494dfe39f339d6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088421"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="10819-102">ICorDebugArrayValue::GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="10819-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="10819-103">取得位於指定位置的專案，將陣列視為以零為基底的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="10819-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10819-104">語法</span><span class="sxs-lookup"><span data-stu-id="10819-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10819-105">參數</span><span class="sxs-lookup"><span data-stu-id="10819-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="10819-106">在要抓取之元素的位置。</span><span class="sxs-lookup"><span data-stu-id="10819-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="10819-107">脫銷ICorDebugValue 物件位址的指標，表示元素的值。</span><span class="sxs-lookup"><span data-stu-id="10819-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10819-108">備註</span><span class="sxs-lookup"><span data-stu-id="10819-108">Remarks</span></span>  
 <span data-ttu-id="10819-109">多維度陣列的配置會遵循陣列版面配置C++的樣式。</span><span class="sxs-lookup"><span data-stu-id="10819-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10819-110">需求</span><span class="sxs-lookup"><span data-stu-id="10819-110">Requirements</span></span>  
 <span data-ttu-id="10819-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10819-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10819-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10819-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10819-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10819-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10819-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10819-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
