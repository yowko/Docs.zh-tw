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
ms.openlocfilehash: 5c9049edd6d139bff29d21b65f9c87ec3e6de1a6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782965"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="e58e7-102">ICorDebugEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="e58e7-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="e58e7-103">在列舉中，將資料指標向後移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="e58e7-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e58e7-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e58e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e58e7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e58e7-106">在要將資料指標向前移動的專案數。</span><span class="sxs-lookup"><span data-stu-id="e58e7-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e58e7-107">需求</span><span class="sxs-lookup"><span data-stu-id="e58e7-107">Requirements</span></span>  
 <span data-ttu-id="e58e7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e58e7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e58e7-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e58e7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e58e7-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e58e7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e58e7-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e58e7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58e7-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e58e7-112">See also</span></span>

- [<span data-ttu-id="e58e7-113">ICorDebugEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e58e7-113">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
