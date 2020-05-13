---
title: ICorDebugThreadEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: c025afac1b53b23636a6160a475704011999d434
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379049"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="97391-102">ICorDebugThreadEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="97391-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="97391-103">從列舉中取得指定之 ICorDebugThread 實例的數目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="97391-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97391-104">語法</span><span class="sxs-lookup"><span data-stu-id="97391-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97391-105">參數</span><span class="sxs-lookup"><span data-stu-id="97391-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="97391-106">在要抓取的 `ICorDebugThread` 實例數目。</span><span class="sxs-lookup"><span data-stu-id="97391-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="97391-107">脫銷指標陣列，其中每一個 `ICorDebugThread` 都會指向代表執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="97391-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="97391-108">脫銷實際傳回之實例數目的指標 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="97391-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="97391-109">如果是一個，這個值可能會是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="97391-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97391-110">需求</span><span class="sxs-lookup"><span data-stu-id="97391-110">Requirements</span></span>  
 <span data-ttu-id="97391-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97391-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97391-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97391-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97391-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97391-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97391-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97391-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
