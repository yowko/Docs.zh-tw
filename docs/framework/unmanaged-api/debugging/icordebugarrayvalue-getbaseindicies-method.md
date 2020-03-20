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
ms.openlocfilehash: 7c6d1905cdbd12b960014e687034ea9d163b68d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179029"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="6d734-102">ICorDebugArrayValue::GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="6d734-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="6d734-103">獲取陣列中每個維度的基本索引。</span><span class="sxs-lookup"><span data-stu-id="6d734-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d734-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d734-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d734-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d734-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="6d734-106">[在]此`ICorDebugArrayValue`物件的維度數。</span><span class="sxs-lookup"><span data-stu-id="6d734-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="6d734-107">此值也是陣列的大小，`indicies`因為它的大小等於`ICorDebugArrayValue`物件的維度數。</span><span class="sxs-lookup"><span data-stu-id="6d734-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="6d734-108">[出]整數陣列，每個陣列都是此`ICorDebugArrayValue`物件維度的基礎索引（即起始索引）。</span><span class="sxs-lookup"><span data-stu-id="6d734-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d734-109">需求</span><span class="sxs-lookup"><span data-stu-id="6d734-109">Requirements</span></span>  
 <span data-ttu-id="6d734-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d734-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d734-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d734-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d734-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d734-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d734-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d734-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
