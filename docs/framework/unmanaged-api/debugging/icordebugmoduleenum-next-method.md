---
title: ICorDebugModuleEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: a4bdac42c584d5d34b072354de65ed20c6a80609
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709488"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="43de1-102">ICorDebugModuleEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="43de1-102">ICorDebugModuleEnum::Next Method</span></span>

<span data-ttu-id="43de1-103">`celt`從目前位置開始，取得從列舉所指定之 "ICorDebugModule" 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="43de1-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43de1-104">語法</span><span class="sxs-lookup"><span data-stu-id="43de1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43de1-105">參數</span><span class="sxs-lookup"><span data-stu-id="43de1-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="43de1-106">在 `ICorDebugModule` 要取出的實例數目。</span><span class="sxs-lookup"><span data-stu-id="43de1-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="43de1-107">擴展指標的陣列，每個指標都會指向一個 `ICorDebugModule` 物件。</span><span class="sxs-lookup"><span data-stu-id="43de1-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="43de1-108">擴展實際傳回之實例數目的指標 `ICorDebugModule` 。</span><span class="sxs-lookup"><span data-stu-id="43de1-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="43de1-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="43de1-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43de1-110">需求</span><span class="sxs-lookup"><span data-stu-id="43de1-110">Requirements</span></span>  

 <span data-ttu-id="43de1-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43de1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43de1-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43de1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43de1-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43de1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43de1-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43de1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43de1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43de1-115">See also</span></span>
