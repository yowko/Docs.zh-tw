---
title: ICorDebugValueEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24507c7cb0860fc04fa519c6bd95113483f629d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174209"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="ec834-102">ICorDebugValueEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="ec834-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="ec834-103">取得指定的數目 」 ICorDebugValue 」 執行個體從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="ec834-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec834-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec834-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec834-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec834-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ec834-106">[in]數目`ICorDebugValue`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ec834-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="ec834-107">[out]指標的陣列，其中每一個指向`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="ec834-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ec834-108">[out]數目的指標`ICorDebugValue`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ec834-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="ec834-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="ec834-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec834-110">需求</span><span class="sxs-lookup"><span data-stu-id="ec834-110">Requirements</span></span>  
 <span data-ttu-id="ec834-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec834-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec834-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec834-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec834-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec834-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ec834-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ec834-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ec834-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec834-115">See also</span></span>
