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
ms.openlocfilehash: ff74a9849b74b8a8e6b8c03f1fc4e7c7eee1ec14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124050"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="1f05d-102">ICorDebugFrameEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="1f05d-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="1f05d-103">從目前的位置開始，取得指定的 ICorDebugFrame 實例數目。</span><span class="sxs-lookup"><span data-stu-id="1f05d-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f05d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f05d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f05d-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f05d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1f05d-106">在要抓取 `ICorDebugFrame` 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="1f05d-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="1f05d-107">脫銷指標陣列，其中每一個都會指向 `ICorDebugFrame` 物件。</span><span class="sxs-lookup"><span data-stu-id="1f05d-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1f05d-108">脫銷實際傳回的 `ICorDebugFrame` 實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="1f05d-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="1f05d-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="1f05d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f05d-110">需求</span><span class="sxs-lookup"><span data-stu-id="1f05d-110">Requirements</span></span>  
 <span data-ttu-id="1f05d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f05d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f05d-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f05d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f05d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f05d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f05d-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f05d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
