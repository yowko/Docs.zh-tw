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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f366a40e1e3cd196f480c5849c49419c7daeea9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480984"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="4e332-102">ICorDebugChain::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="4e332-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="4e332-103">取得設定此鏈結的使用中部分的暫存器。</span><span class="sxs-lookup"><span data-stu-id="4e332-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e332-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e332-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e332-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e332-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="4e332-106">[out]位址指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)物件，表示將暫存器集的這個鏈結作用中的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e332-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e332-107">需求</span><span class="sxs-lookup"><span data-stu-id="4e332-107">Requirements</span></span>  
 <span data-ttu-id="4e332-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e332-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e332-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e332-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e332-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e332-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e332-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e332-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
