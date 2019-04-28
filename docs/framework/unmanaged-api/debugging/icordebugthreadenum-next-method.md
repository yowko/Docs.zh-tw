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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b80e0cc026ce80950c14436abb2e84548f9adb64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903314"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="71788-102">ICorDebugThreadEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="71788-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="71788-103">取得指定 ICorDebugThread 執行個體數目，從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="71788-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71788-104">語法</span><span class="sxs-lookup"><span data-stu-id="71788-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71788-105">參數</span><span class="sxs-lookup"><span data-stu-id="71788-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="71788-106">[in]數目`ICorDebugThread`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="71788-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="71788-107">[out]指標的陣列，其中每一個指向`ICorDebugThread`物件，表示執行緒。</span><span class="sxs-lookup"><span data-stu-id="71788-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="71788-108">[out]數目的指標`ICorDebugThread`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="71788-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="71788-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="71788-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71788-110">需求</span><span class="sxs-lookup"><span data-stu-id="71788-110">Requirements</span></span>  
 <span data-ttu-id="71788-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71788-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71788-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71788-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71788-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71788-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71788-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71788-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
