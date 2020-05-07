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
ms.openlocfilehash: 5644c20ec5df2606c7258131573691997f424e50
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895018"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="a073d-102">ICorDebugArrayValue::GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="a073d-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="a073d-103">取得位於指定位置的專案，將陣列視為以零為基底的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="a073d-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a073d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a073d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a073d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a073d-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="a073d-106">在要抓取之元素的位置。</span><span class="sxs-lookup"><span data-stu-id="a073d-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a073d-107">脫銷ICorDebugValue 物件位址的指標，表示元素的值。</span><span class="sxs-lookup"><span data-stu-id="a073d-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a073d-108">備註</span><span class="sxs-lookup"><span data-stu-id="a073d-108">Remarks</span></span>  
 <span data-ttu-id="a073d-109">多維度陣列的配置會遵循陣列版面配置的 c + + 樣式。</span><span class="sxs-lookup"><span data-stu-id="a073d-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a073d-110">需求</span><span class="sxs-lookup"><span data-stu-id="a073d-110">Requirements</span></span>  
 <span data-ttu-id="a073d-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a073d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a073d-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a073d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a073d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a073d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a073d-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a073d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
