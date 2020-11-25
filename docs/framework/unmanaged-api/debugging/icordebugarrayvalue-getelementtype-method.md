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
ms.openlocfilehash: 1deadef7517772460adc96cd0dd630d85cb21c9f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698150"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="861b1-102">ICorDebugArrayValue::GetElementType 方法</span><span class="sxs-lookup"><span data-stu-id="861b1-102">ICorDebugArrayValue::GetElementType Method</span></span>

<span data-ttu-id="861b1-103">取得值，指出陣列中元素的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="861b1-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="861b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="861b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="861b1-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="861b1-106">擴展CorElementType 列舉值的指標，指出型別。</span><span class="sxs-lookup"><span data-stu-id="861b1-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="861b1-107">需求</span><span class="sxs-lookup"><span data-stu-id="861b1-107">Requirements</span></span>  

 <span data-ttu-id="861b1-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="861b1-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="861b1-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="861b1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="861b1-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="861b1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="861b1-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="861b1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
