---
title: ICorDebugEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e2d7a344cabb1ab816e4fe696ebb47276397ec3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095031"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="00ed7-102">ICorDebugEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="00ed7-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="00ed7-103">將游標移往前列舉中所指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="00ed7-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ed7-104">語法</span><span class="sxs-lookup"><span data-stu-id="00ed7-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00ed7-105">參數</span><span class="sxs-lookup"><span data-stu-id="00ed7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="00ed7-106">[in]用來將游標向前移動的項目數目。</span><span class="sxs-lookup"><span data-stu-id="00ed7-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ed7-107">需求</span><span class="sxs-lookup"><span data-stu-id="00ed7-107">Requirements</span></span>  
 <span data-ttu-id="00ed7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00ed7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00ed7-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00ed7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00ed7-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00ed7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00ed7-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00ed7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ed7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00ed7-112">See also</span></span>

- [<span data-ttu-id="00ed7-113">ICorDebugEnum 介面</span><span class="sxs-lookup"><span data-stu-id="00ed7-113">ICorDebugEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
