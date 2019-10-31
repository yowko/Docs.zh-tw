---
title: ICorDebugValueEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: 09394acb07b8595f99d9ecc873eb0985cdd79316
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134589"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="be1ff-102">ICorDebugValueEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="be1ff-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="be1ff-103">從列舉中取得指定數目的 "ICorDebugValue" 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="be1ff-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="be1ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be1ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="be1ff-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="be1ff-106">在要抓取 `ICorDebugValue` 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="be1ff-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="be1ff-107">脫銷指標陣列，其中每一個都會指向 `ICorDebugValue` 物件。</span><span class="sxs-lookup"><span data-stu-id="be1ff-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="be1ff-108">脫銷實際傳回的 `ICorDebugValue` 實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="be1ff-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="be1ff-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="be1ff-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be1ff-110">需求</span><span class="sxs-lookup"><span data-stu-id="be1ff-110">Requirements</span></span>  
 <span data-ttu-id="be1ff-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be1ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be1ff-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be1ff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be1ff-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be1ff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be1ff-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be1ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1ff-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="be1ff-115">See also</span></span>
