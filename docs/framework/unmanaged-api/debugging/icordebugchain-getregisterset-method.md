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
ms.openlocfilehash: a3f02af1a0de9fcd7b3db1e49ef0d78af3395d2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719654"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="14376-102">ICorDebugChain::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="14376-102">ICorDebugChain::GetRegisterSet Method</span></span>

<span data-ttu-id="14376-103">取得此鏈之使用中部分的註冊集。</span><span class="sxs-lookup"><span data-stu-id="14376-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14376-104">語法</span><span class="sxs-lookup"><span data-stu-id="14376-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14376-105">參數</span><span class="sxs-lookup"><span data-stu-id="14376-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="14376-106">擴展 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 物件位址的指標，該物件代表此鏈之使用中部分的註冊集。</span><span class="sxs-lookup"><span data-stu-id="14376-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14376-107">需求</span><span class="sxs-lookup"><span data-stu-id="14376-107">Requirements</span></span>  

 <span data-ttu-id="14376-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14376-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14376-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14376-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14376-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14376-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14376-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14376-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
