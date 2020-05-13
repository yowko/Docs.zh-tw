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
ms.openlocfilehash: d7ad4a6b25fe6d53ab0b21066345451ae7c22c16
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213318"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="3ce31-102">ICorDebugModuleEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="3ce31-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="3ce31-103">`celt`從目前位置開始，取得列舉中所指定的 "ICorDebugModule" 實例數目。</span><span class="sxs-lookup"><span data-stu-id="3ce31-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce31-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ce31-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ce31-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ce31-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3ce31-106">在要抓取的 `ICorDebugModule` 實例數目。</span><span class="sxs-lookup"><span data-stu-id="3ce31-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="3ce31-107">脫銷指標陣列，其中每一個都會指向一個 `ICorDebugModule` 物件。</span><span class="sxs-lookup"><span data-stu-id="3ce31-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3ce31-108">脫銷實際傳回之實例數目的指標 `ICorDebugModule` 。</span><span class="sxs-lookup"><span data-stu-id="3ce31-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="3ce31-109">如果是一個，這個值可能會是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="3ce31-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce31-110">需求</span><span class="sxs-lookup"><span data-stu-id="3ce31-110">Requirements</span></span>  
 <span data-ttu-id="3ce31-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce31-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ce31-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ce31-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ce31-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ce31-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ce31-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ce31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce31-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce31-115">See also</span></span>
