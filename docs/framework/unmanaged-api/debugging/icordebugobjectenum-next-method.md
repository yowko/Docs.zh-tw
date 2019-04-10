---
title: ICorDebugObjectEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6998be3daf0ab6a6290a3400b96c32227df3e022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175082"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="422e8-102">ICorDebugObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="422e8-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="422e8-103">取得列舉型別，從目前位置開始的指定數目物件的相對虛擬位址 (Rva)。</span><span class="sxs-lookup"><span data-stu-id="422e8-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="422e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="422e8-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="422e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="422e8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="422e8-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="422e8-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="422e8-107">[out]指標的陣列，其中每一個指向 CORDB_ADDRESS 物件。</span><span class="sxs-lookup"><span data-stu-id="422e8-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="422e8-108">[out]實際傳回的物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="422e8-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="422e8-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="422e8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="422e8-110">需求</span><span class="sxs-lookup"><span data-stu-id="422e8-110">Requirements</span></span>  
 <span data-ttu-id="422e8-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="422e8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="422e8-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="422e8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="422e8-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="422e8-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="422e8-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="422e8-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="422e8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="422e8-115">See also</span></span>
