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
ms.openlocfilehash: bfdde1f29300fcdc0f4e267949fdc3f6fd9917ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401404"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="dc9f6-102">ICorDebugChain::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="dc9f6-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="dc9f6-103">取得為這個鏈結的使用中部分設定的暫存器。</span><span class="sxs-lookup"><span data-stu-id="dc9f6-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc9f6-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc9f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc9f6-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="dc9f6-106">[out]位址指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)這個鏈結的使用中部分設定物件，代表暫存器。</span><span class="sxs-lookup"><span data-stu-id="dc9f6-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc9f6-107">需求</span><span class="sxs-lookup"><span data-stu-id="dc9f6-107">Requirements</span></span>  
 <span data-ttu-id="dc9f6-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc9f6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc9f6-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc9f6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc9f6-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc9f6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc9f6-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc9f6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
