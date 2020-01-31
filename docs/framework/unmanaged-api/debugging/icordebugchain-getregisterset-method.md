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
ms.openlocfilehash: 1a435226fca775d7dd38a4c5dd35eac3078b092b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784291"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="a3300-102">ICorDebugChain::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="a3300-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="a3300-103">取得此連鎖之使用中部分的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="a3300-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3300-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3300-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3300-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3300-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="a3300-106">脫銷[ICorDebugRegisterSet](icordebugregisterset-interface.md)物件位址的指標，表示此鏈中使用中部分的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="a3300-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3300-107">需求</span><span class="sxs-lookup"><span data-stu-id="a3300-107">Requirements</span></span>  
 <span data-ttu-id="a3300-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3300-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3300-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3300-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3300-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3300-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3300-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3300-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
