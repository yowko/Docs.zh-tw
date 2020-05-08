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
ms.openlocfilehash: 9aadbe7c6f18c6b15350267d1f9ecaa3a23cdd20
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895074"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="fcc7f-102">ICorDebugArrayValue::GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="fcc7f-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="fcc7f-103">取得陣列中每個維度的基底索引。</span><span class="sxs-lookup"><span data-stu-id="fcc7f-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcc7f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcc7f-105">參數</span><span class="sxs-lookup"><span data-stu-id="fcc7f-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="fcc7f-106">在這個`ICorDebugArrayValue`物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="fcc7f-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="fcc7f-107">這個值也是`indicies`陣列的大小，因為它的大小等於`ICorDebugArrayValue`物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="fcc7f-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="fcc7f-108">脫銷整數的陣列，其中每一個都是這個`ICorDebugArrayValue`物件之維度的基底索引（也就是起始索引）。</span><span class="sxs-lookup"><span data-stu-id="fcc7f-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc7f-109">需求</span><span class="sxs-lookup"><span data-stu-id="fcc7f-109">Requirements</span></span>  
 <span data-ttu-id="fcc7f-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc7f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc7f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcc7f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcc7f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcc7f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcc7f-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc7f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
