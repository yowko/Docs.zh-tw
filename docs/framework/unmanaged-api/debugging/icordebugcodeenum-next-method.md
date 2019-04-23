---
title: ICorDebugCodeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5db87cd4ad965654b63a68828cd088b8d2f7d07c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113044"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="90f00-102">ICorDebugCodeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="90f00-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="90f00-103">取得指定的數目 」 ICorDebugCode 」 執行個體從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="90f00-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90f00-104">語法</span><span class="sxs-lookup"><span data-stu-id="90f00-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90f00-105">參數</span><span class="sxs-lookup"><span data-stu-id="90f00-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="90f00-106">[in]數目`ICorDebugCode`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="90f00-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="90f00-107">[out]指標的陣列，其中每一個指向`ICorDebugCode`物件。</span><span class="sxs-lookup"><span data-stu-id="90f00-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="90f00-108">[out]數目的指標`ICorDebugCode`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="90f00-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="90f00-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="90f00-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90f00-110">需求</span><span class="sxs-lookup"><span data-stu-id="90f00-110">Requirements</span></span>  
 <span data-ttu-id="90f00-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90f00-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90f00-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90f00-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90f00-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90f00-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90f00-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90f00-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f00-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90f00-115">See also</span></span>
