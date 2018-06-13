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
ms.openlocfilehash: 580c7b4dcd63f83e113a5317c242b7e66cfb3f5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403412"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="bcdfe-102">ICorDebugArrayValue::GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="bcdfe-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="bcdfe-103">取得陣列視為的以零為起始的一維陣列的指定位置處的元素。</span><span class="sxs-lookup"><span data-stu-id="bcdfe-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcdfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="bcdfe-104">Syntax</span></span>  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcdfe-105">參數</span><span class="sxs-lookup"><span data-stu-id="bcdfe-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="bcdfe-106">[in]要擷取之項目的位置。</span><span class="sxs-lookup"><span data-stu-id="bcdfe-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bcdfe-107">[out]ICorDebugValue 物件，表示項目的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="bcdfe-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcdfe-108">備註</span><span class="sxs-lookup"><span data-stu-id="bcdfe-108">Remarks</span></span>  
 <span data-ttu-id="bcdfe-109">多維度陣列的配置會遵循陣列配置的 c + + 樣式。</span><span class="sxs-lookup"><span data-stu-id="bcdfe-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcdfe-110">需求</span><span class="sxs-lookup"><span data-stu-id="bcdfe-110">Requirements</span></span>  
 <span data-ttu-id="bcdfe-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcdfe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcdfe-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcdfe-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcdfe-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcdfe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcdfe-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcdfe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
