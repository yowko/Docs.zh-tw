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
ms.openlocfilehash: 9d8bd6ab13fa408fd7390aaeb76baee274742f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137695"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="42913-102">ICorDebugRegisterSet::GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="42913-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="42913-103">取得位元遮罩，指出目前可使用此[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)中的哪些暫存器。</span><span class="sxs-lookup"><span data-stu-id="42913-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42913-104">語法</span><span class="sxs-lookup"><span data-stu-id="42913-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42913-105">參數</span><span class="sxs-lookup"><span data-stu-id="42913-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="42913-106">脫銷位元遮罩，指出目前可使用的暫存器。</span><span class="sxs-lookup"><span data-stu-id="42913-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42913-107">備註</span><span class="sxs-lookup"><span data-stu-id="42913-107">Remarks</span></span>  
 <span data-ttu-id="42913-108">如果無法判斷指定狀況的值，暫存器可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="42913-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="42913-109">傳回的遮罩會包含每個暫存器的位（1 < < 暫存器索引）。</span><span class="sxs-lookup"><span data-stu-id="42913-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="42913-110">如果註冊可供使用，位值是1，如果無法使用，則為0。</span><span class="sxs-lookup"><span data-stu-id="42913-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42913-111">需求</span><span class="sxs-lookup"><span data-stu-id="42913-111">Requirements</span></span>  
 <span data-ttu-id="42913-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42913-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42913-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42913-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42913-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42913-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42913-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42913-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42913-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="42913-116">See also</span></span>

- [<span data-ttu-id="42913-117">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="42913-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="42913-118">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="42913-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
