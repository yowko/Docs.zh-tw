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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68098895b2ad7f5c08d30f222777e52d4ee3f063
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476655"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="67d41-102">ICorDebugFrameEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="67d41-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="67d41-103">取得指定的數目的 ICorDebugFrame 執行個體，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="67d41-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67d41-104">語法</span><span class="sxs-lookup"><span data-stu-id="67d41-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67d41-105">參數</span><span class="sxs-lookup"><span data-stu-id="67d41-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="67d41-106">[in]數目`ICorDebugFrame`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="67d41-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="67d41-107">[out]指標的陣列，其中每一個指向`ICorDebugFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="67d41-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="67d41-108">[out]數目的指標`ICorDebugFrame`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="67d41-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="67d41-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="67d41-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67d41-110">需求</span><span class="sxs-lookup"><span data-stu-id="67d41-110">Requirements</span></span>  
 <span data-ttu-id="67d41-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67d41-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d41-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67d41-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67d41-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67d41-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67d41-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d41-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
