---
title: ICorDebugArrayValue::GetBaseIndicies 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f24a1434f737e8281a0c68dd09d2e17b34371694
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471650"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="ae003-102">ICorDebugArrayValue::GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="ae003-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="ae003-103">取得陣列中的每個維度的基底的索引。</span><span class="sxs-lookup"><span data-stu-id="ae003-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae003-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae003-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae003-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae003-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="ae003-106">[in]這個維度的數目`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="ae003-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="ae003-107">此值也是的大小`indicies`因為其大小的維度數目等於陣列`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="ae003-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="ae003-108">[out]整數的陣列，每個都是這個維度的基底的索引 （也就是說，起始的索引）`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="ae003-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae003-109">需求</span><span class="sxs-lookup"><span data-stu-id="ae003-109">Requirements</span></span>  
 <span data-ttu-id="ae003-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae003-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae003-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae003-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae003-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae003-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae003-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae003-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
