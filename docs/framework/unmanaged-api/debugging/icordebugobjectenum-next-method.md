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
ms.openlocfilehash: 5a5f21855ce83f5c1fb68637e3eeb6d3c831bce2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745142"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="6f764-102">ICorDebugObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="6f764-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="6f764-103">取得列舉型別，從目前位置開始的指定數目物件的相對虛擬位址 (Rva)。</span><span class="sxs-lookup"><span data-stu-id="6f764-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f764-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f764-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f764-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f764-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6f764-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="6f764-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6f764-107">[out]指標的陣列，其中每一個指向 CORDB_ADDRESS 物件。</span><span class="sxs-lookup"><span data-stu-id="6f764-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6f764-108">[out]實際傳回的物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="6f764-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="6f764-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="6f764-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f764-110">需求</span><span class="sxs-lookup"><span data-stu-id="6f764-110">Requirements</span></span>  
 <span data-ttu-id="6f764-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f764-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f764-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f764-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f764-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f764-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f764-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f764-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f764-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f764-115">See also</span></span>

