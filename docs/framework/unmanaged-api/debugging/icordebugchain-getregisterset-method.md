---
title: ICorDebugChain::GetRegisterSet 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
ms.openlocfilehash: d6ee36ac4d4510637e5f8240c3b8930a9bec7970
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123837"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="72e5b-102">ICorDebugChain::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="72e5b-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="72e5b-103">取得此連鎖之使用中部分的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="72e5b-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="72e5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72e5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="72e5b-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="72e5b-106">脫銷[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)物件位址的指標，表示此鏈中使用中部分的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="72e5b-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e5b-107">需求</span><span class="sxs-lookup"><span data-stu-id="72e5b-107">Requirements</span></span>  
 <span data-ttu-id="72e5b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72e5b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72e5b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72e5b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72e5b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72e5b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72e5b-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72e5b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
