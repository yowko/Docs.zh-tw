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
ms.openlocfilehash: 6c4262c18e4efcbbca1b3e2a327fec7d4b609a31
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096919"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="54017-102">ICorDebugModuleEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="54017-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="54017-103">從目前位置開始，取得列舉中 `celt` 所指定的 "ICorDebugModule" 實例數目。</span><span class="sxs-lookup"><span data-stu-id="54017-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54017-104">語法</span><span class="sxs-lookup"><span data-stu-id="54017-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54017-105">參數</span><span class="sxs-lookup"><span data-stu-id="54017-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="54017-106">在要抓取 `ICorDebugModule` 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="54017-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="54017-107">脫銷指標陣列，其中每一個都會指向 `ICorDebugModule` 物件。</span><span class="sxs-lookup"><span data-stu-id="54017-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="54017-108">脫銷實際傳回的 `ICorDebugModule` 實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="54017-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="54017-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="54017-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54017-110">需求</span><span class="sxs-lookup"><span data-stu-id="54017-110">Requirements</span></span>  
 <span data-ttu-id="54017-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54017-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54017-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54017-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54017-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54017-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54017-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54017-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54017-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="54017-115">See also</span></span>
