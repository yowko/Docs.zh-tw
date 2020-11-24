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
ms.openlocfilehash: e1c8d94a90092b1497267c78d5fadf5a6e6de707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684326"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="9df59-102">ICorDebugValueEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="9df59-102">ICorDebugValueEnum::Next Method</span></span>

<span data-ttu-id="9df59-103">從目前位置開始，取得列舉中指定的 "ICorDebugValue" 實例數目。</span><span class="sxs-lookup"><span data-stu-id="9df59-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df59-104">語法</span><span class="sxs-lookup"><span data-stu-id="9df59-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9df59-105">參數</span><span class="sxs-lookup"><span data-stu-id="9df59-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="9df59-106">在 `ICorDebugValue` 要取出的實例數目。</span><span class="sxs-lookup"><span data-stu-id="9df59-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9df59-107">擴展指標的陣列，每個指標都會指向一個 `ICorDebugValue` 物件。</span><span class="sxs-lookup"><span data-stu-id="9df59-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9df59-108">擴展實際傳回之實例數目的指標 `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="9df59-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="9df59-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="9df59-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9df59-110">需求</span><span class="sxs-lookup"><span data-stu-id="9df59-110">Requirements</span></span>  

 <span data-ttu-id="9df59-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9df59-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9df59-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9df59-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9df59-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9df59-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9df59-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9df59-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df59-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9df59-115">See also</span></span>
