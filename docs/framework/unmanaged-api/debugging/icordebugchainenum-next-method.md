---
title: ICorDebugChainEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 2d075820df534e08bdf4c2b75d36f6a60f979662
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894099"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="5c245-102">ICorDebugChainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="5c245-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="5c245-103">從列舉中取得指定數目的 ICorDebugChain 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="5c245-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c245-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c245-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c245-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c245-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5c245-106">在要抓取的`ICorDebugChain`實例數目。</span><span class="sxs-lookup"><span data-stu-id="5c245-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="5c245-107">脫銷指標陣列，其中每一個都會指向代表一個鏈`ICorDebugChain`的物件。</span><span class="sxs-lookup"><span data-stu-id="5c245-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5c245-108">脫銷實際傳回之`ICorDebugChain`實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="5c245-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="5c245-109">如果`celt`是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="5c245-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c245-110">需求</span><span class="sxs-lookup"><span data-stu-id="5c245-110">Requirements</span></span>  
 <span data-ttu-id="5c245-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c245-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c245-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c245-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c245-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c245-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c245-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c245-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
