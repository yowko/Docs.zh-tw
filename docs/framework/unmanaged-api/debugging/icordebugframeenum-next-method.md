---
title: ICorDebugFrameEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 4652e4b34d614ad3b7b852925fcc63309bdd1498
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209457"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="c9fff-102">ICorDebugFrameEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="c9fff-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="c9fff-103">從目前的位置開始，取得指定的 ICorDebugFrame 實例數目。</span><span class="sxs-lookup"><span data-stu-id="c9fff-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9fff-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9fff-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9fff-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9fff-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c9fff-106">在要抓取的 `ICorDebugFrame` 實例數目。</span><span class="sxs-lookup"><span data-stu-id="c9fff-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="c9fff-107">脫銷指標陣列，其中每一個都會指向一個 `ICorDebugFrame` 物件。</span><span class="sxs-lookup"><span data-stu-id="c9fff-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c9fff-108">脫銷實際傳回之實例數目的指標 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="c9fff-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="c9fff-109">如果是一個，這個值可能會是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="c9fff-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9fff-110">需求</span><span class="sxs-lookup"><span data-stu-id="c9fff-110">Requirements</span></span>  
 <span data-ttu-id="c9fff-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9fff-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9fff-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9fff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9fff-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9fff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9fff-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9fff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
