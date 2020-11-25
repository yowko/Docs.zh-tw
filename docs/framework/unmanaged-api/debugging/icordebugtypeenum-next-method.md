---
title: ICorDebugTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: 78ea76033b0b83c84446e16fb330bd3ba34c6e21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725699"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="34317-102">ICorDebugTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="34317-102">ICorDebugTypeEnum::Next Method</span></span>

<span data-ttu-id="34317-103">`celt`從目前位置開始，取得從列舉所指定之 "ICorDebugType" 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="34317-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34317-104">語法</span><span class="sxs-lookup"><span data-stu-id="34317-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34317-105">參數</span><span class="sxs-lookup"><span data-stu-id="34317-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="34317-106">在 `ICorDebugType` 要取出的實例數目。</span><span class="sxs-lookup"><span data-stu-id="34317-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="34317-107">擴展指標的陣列，每個指標都會指向一個 `ICorDebugType` 物件。</span><span class="sxs-lookup"><span data-stu-id="34317-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="34317-108">擴展實際傳回之實例數目的指標 `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="34317-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="34317-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="34317-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34317-110">需求</span><span class="sxs-lookup"><span data-stu-id="34317-110">Requirements</span></span>  

 <span data-ttu-id="34317-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34317-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34317-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34317-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34317-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34317-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34317-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34317-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34317-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34317-115">See also</span></span>
