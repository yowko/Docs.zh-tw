---
title: ICorDebugRegisterSet::GetRegistersAvailable 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f341098268f735a576bdbc5f0cea52f1a7e14f90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156035"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="699be-102">ICorDebugRegisterSet::GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="699be-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="699be-103">取得位元遮罩，指出其會登錄在此[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)目前可用。</span><span class="sxs-lookup"><span data-stu-id="699be-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="699be-104">語法</span><span class="sxs-lookup"><span data-stu-id="699be-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="699be-105">參數</span><span class="sxs-lookup"><span data-stu-id="699be-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="699be-106">[out]位元遮罩，指出目前使用哪些暫存器。</span><span class="sxs-lookup"><span data-stu-id="699be-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="699be-107">備註</span><span class="sxs-lookup"><span data-stu-id="699be-107">Remarks</span></span>  
 <span data-ttu-id="699be-108">暫存器可能無法使用，如果其值無法判斷指定的情況。</span><span class="sxs-lookup"><span data-stu-id="699be-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="699be-109">傳回的遮罩位元包含每個暫存器 (1 << 暫存索引)。</span><span class="sxs-lookup"><span data-stu-id="699be-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="699be-110">位元值為 1，如果將暫存器可供使用，則為 0，如果它無法使用。</span><span class="sxs-lookup"><span data-stu-id="699be-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="699be-111">需求</span><span class="sxs-lookup"><span data-stu-id="699be-111">Requirements</span></span>  
 <span data-ttu-id="699be-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="699be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="699be-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="699be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="699be-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="699be-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="699be-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="699be-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="699be-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="699be-116">See also</span></span>

- [<span data-ttu-id="699be-117">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="699be-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="699be-118">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="699be-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
