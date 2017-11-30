---
title: "ICorDebugRegisterSet::GetRegistersAvailable 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa4dd904b07aa2c9157e61e6968e96ef797ad3f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="bfbbb-102">ICorDebugRegisterSet::GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="bfbbb-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="bfbbb-103">取得位元遮罩，指出其會登錄在這個[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)目前可用。</span><span class="sxs-lookup"><span data-stu-id="bfbbb-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfbbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfbbb-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfbbb-105">參數</span><span class="sxs-lookup"><span data-stu-id="bfbbb-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="bfbbb-106">[out]位元遮罩，指出哪些暫存器是目前可用。</span><span class="sxs-lookup"><span data-stu-id="bfbbb-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfbbb-107">備註</span><span class="sxs-lookup"><span data-stu-id="bfbbb-107">Remarks</span></span>  
 <span data-ttu-id="bfbbb-108">暫存器可能無法使用，如果無法判別其值，指定的情況。</span><span class="sxs-lookup"><span data-stu-id="bfbbb-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="bfbbb-109">傳回的遮罩的位元包含每個暫存器 (1 << 暫存索引)。</span><span class="sxs-lookup"><span data-stu-id="bfbbb-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="bfbbb-110">位元值為 1，如果暫存器可用，則為 0，如果無法使用。</span><span class="sxs-lookup"><span data-stu-id="bfbbb-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfbbb-111">需求</span><span class="sxs-lookup"><span data-stu-id="bfbbb-111">Requirements</span></span>  
 <span data-ttu-id="bfbbb-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfbbb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfbbb-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfbbb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfbbb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfbbb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfbbb-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfbbb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfbbb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfbbb-116">See Also</span></span>  
 [<span data-ttu-id="bfbbb-117">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="bfbbb-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="bfbbb-118">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="bfbbb-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
