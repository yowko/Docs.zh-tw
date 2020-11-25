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
ms.openlocfilehash: 76b96dfd9d22c7e770671dcc01cb421430df729f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728182"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="dc562-102">ICorDebugFrameEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="dc562-102">ICorDebugFrameEnum::Next Method</span></span>

<span data-ttu-id="dc562-103">從目前位置開始取得指定數目的 ICorDebugFrame 實例。</span><span class="sxs-lookup"><span data-stu-id="dc562-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc562-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc562-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc562-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc562-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="dc562-106">在 `ICorDebugFrame` 要取出的實例數目。</span><span class="sxs-lookup"><span data-stu-id="dc562-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="dc562-107">擴展指標的陣列，每個指標都會指向一個 `ICorDebugFrame` 物件。</span><span class="sxs-lookup"><span data-stu-id="dc562-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dc562-108">擴展實際傳回之實例數目的指標 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="dc562-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="dc562-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="dc562-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc562-110">需求</span><span class="sxs-lookup"><span data-stu-id="dc562-110">Requirements</span></span>  

 <span data-ttu-id="dc562-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc562-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc562-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc562-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc562-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc562-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc562-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc562-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
