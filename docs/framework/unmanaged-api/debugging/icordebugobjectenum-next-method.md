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
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178694"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="8a6c9-102">ICorDebugObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="8a6c9-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="8a6c9-103">從枚舉中獲取指定數量的物件的相對虛擬位址 （RVA），從當前位置開始。</span><span class="sxs-lookup"><span data-stu-id="8a6c9-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a6c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a6c9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a6c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a6c9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8a6c9-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="8a6c9-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="8a6c9-107">[出]指標陣列，每個指標都指向CORDB_ADDRESS物件。</span><span class="sxs-lookup"><span data-stu-id="8a6c9-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8a6c9-108">[出]指向實際返回的物件數的指標。</span><span class="sxs-lookup"><span data-stu-id="8a6c9-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="8a6c9-109">此值可以是 null（如果是`celt`1）。</span><span class="sxs-lookup"><span data-stu-id="8a6c9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a6c9-110">需求</span><span class="sxs-lookup"><span data-stu-id="8a6c9-110">Requirements</span></span>  
 <span data-ttu-id="8a6c9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a6c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a6c9-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a6c9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a6c9-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a6c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a6c9-114">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a6c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a6c9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a6c9-115">See also</span></span>
