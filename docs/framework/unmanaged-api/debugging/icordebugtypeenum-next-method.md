---
title: ICorDebugTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf70d8665d3984c379da9d9058cd97315def7b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677676"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="2927c-102">ICorDebugTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="2927c-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="2927c-103">取得所指定的 「 ICorDebugType 」 執行個體數目`celt`從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="2927c-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2927c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2927c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2927c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2927c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2927c-106">[in]數目`ICorDebugType`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2927c-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="2927c-107">[out]指標的陣列，其中每一個指向`ICorDebugType`物件。</span><span class="sxs-lookup"><span data-stu-id="2927c-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2927c-108">[out]數目的指標`ICorDebugType`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2927c-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="2927c-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="2927c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2927c-110">需求</span><span class="sxs-lookup"><span data-stu-id="2927c-110">Requirements</span></span>  
 <span data-ttu-id="2927c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2927c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2927c-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2927c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2927c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2927c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2927c-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2927c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2927c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2927c-115">See also</span></span>

