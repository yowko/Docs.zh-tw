---
title: ICorDebugModuleEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7624a22e5d65ae94797779a0b8cfa70f226450ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418980"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="7b219-102">ICorDebugModuleEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="7b219-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="7b219-103">取得所指定的"ICorDebugModule 」 執行個體數目`celt`列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="7b219-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b219-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b219-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b219-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b219-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7b219-106">[in]數目`ICorDebugModule`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b219-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="7b219-107">[out]陣列的指標，其中每個指向`ICorDebugModule`物件。</span><span class="sxs-lookup"><span data-stu-id="7b219-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7b219-108">[out]指標的數目`ICorDebugModule`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b219-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="7b219-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="7b219-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b219-110">需求</span><span class="sxs-lookup"><span data-stu-id="7b219-110">Requirements</span></span>  
 <span data-ttu-id="7b219-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b219-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b219-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b219-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b219-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b219-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b219-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b219-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b219-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b219-115">See Also</span></span>  
 
