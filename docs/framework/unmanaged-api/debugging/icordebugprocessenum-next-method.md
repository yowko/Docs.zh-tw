---
title: ICorDebugProcessEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: 6aee88452819a4aabe2a29971ce86079ef7f0008
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732498"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="7bbfa-102">ICorDebugProcessEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="7bbfa-102">ICorDebugProcessEnum::Next Method</span></span>

<span data-ttu-id="7bbfa-103">從目前位置開始，取得列舉中指定的 ICorDebugProcess 實例數目。</span><span class="sxs-lookup"><span data-stu-id="7bbfa-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bbfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bbfa-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bbfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bbfa-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="7bbfa-106">在 `ICorDebugProcess` 要取出的實例數目。</span><span class="sxs-lookup"><span data-stu-id="7bbfa-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="7bbfa-107">擴展指標的陣列，每個指標 `ICorDebugProcess` 都會指向代表進程的物件。</span><span class="sxs-lookup"><span data-stu-id="7bbfa-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7bbfa-108">擴展實際傳回之實例數目的指標 `ICorDebugProcess` 。</span><span class="sxs-lookup"><span data-stu-id="7bbfa-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="7bbfa-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="7bbfa-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bbfa-110">需求</span><span class="sxs-lookup"><span data-stu-id="7bbfa-110">Requirements</span></span>  

 <span data-ttu-id="7bbfa-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bbfa-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bbfa-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bbfa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bbfa-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bbfa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bbfa-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bbfa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
