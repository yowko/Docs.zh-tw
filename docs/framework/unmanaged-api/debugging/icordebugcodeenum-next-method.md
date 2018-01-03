---
title: "ICorDebugCodeEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCodeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dbc7985ebf2fff5fa0c5b524b8d6560f75318d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="ea837-102">ICorDebugCodeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="ea837-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="ea837-103">取得"ICorDebugCode 」 執行個體的指定的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="ea837-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea837-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea837-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea837-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea837-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ea837-106">[in]數目`ICorDebugCode`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea837-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="ea837-107">[out]陣列的指標，其中每個指向`ICorDebugCode`物件。</span><span class="sxs-lookup"><span data-stu-id="ea837-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ea837-108">[out]數目的指標`ICorDebugCode`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea837-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="ea837-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="ea837-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea837-110">需求</span><span class="sxs-lookup"><span data-stu-id="ea837-110">Requirements</span></span>  
 <span data-ttu-id="ea837-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea837-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea837-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea837-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea837-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea837-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea837-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea837-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea837-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea837-115">See Also</span></span>  
    
 
