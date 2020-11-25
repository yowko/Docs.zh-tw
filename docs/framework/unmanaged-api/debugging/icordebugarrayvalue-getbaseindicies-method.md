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
ms.openlocfilehash: ea5c5a728afb9ac90f8599c833caab11fd0c65fe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731458"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="059a8-102">ICorDebugArrayValue::GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="059a8-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>

<span data-ttu-id="059a8-103">取得陣列中每個維度的基底索引。</span><span class="sxs-lookup"><span data-stu-id="059a8-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="059a8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="059a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="059a8-105">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="059a8-106">在此物件的維度數目 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="059a8-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="059a8-107">此值也是陣列的大小， `indicies` 因為其大小等於物件的維度數目 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="059a8-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="059a8-108">擴展整數陣列，其中每一個都是基底索引， (也就是這個物件之維度的開始索引) `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="059a8-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="059a8-109">需求</span><span class="sxs-lookup"><span data-stu-id="059a8-109">Requirements</span></span>  

 <span data-ttu-id="059a8-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="059a8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="059a8-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="059a8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="059a8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="059a8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="059a8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="059a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
