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
ms.openlocfilehash: a6e5ecee9a89da98a73dfb20935c5ec594d5958f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732927"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="4fead-102">ICorDebugArrayValue::GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="4fead-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>

<span data-ttu-id="4fead-103">取得指定位置的專案，將陣列視為以零為基礎的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="4fead-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fead-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fead-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fead-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fead-105">Parameters</span></span>  

 `nPosition`  
 <span data-ttu-id="4fead-106">在要抓取之元素的位置。</span><span class="sxs-lookup"><span data-stu-id="4fead-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4fead-107">擴展ICorDebugValue 物件位址的指標，該物件代表元素的值。</span><span class="sxs-lookup"><span data-stu-id="4fead-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fead-108">備註</span><span class="sxs-lookup"><span data-stu-id="4fead-108">Remarks</span></span>  

 <span data-ttu-id="4fead-109">多維度陣列的版面配置會遵循 c + + 的陣列配置樣式。</span><span class="sxs-lookup"><span data-stu-id="4fead-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fead-110">需求</span><span class="sxs-lookup"><span data-stu-id="4fead-110">Requirements</span></span>  

 <span data-ttu-id="4fead-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fead-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fead-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fead-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fead-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fead-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fead-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fead-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
