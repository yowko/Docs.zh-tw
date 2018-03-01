---
title: "ICorDebugChain::GetCaller 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17c55358a1d502ce5946617556222282ac4c4fca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="266dd-102">ICorDebugChain::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="266dd-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="266dd-103">取得呼叫這個鏈結的鏈結。</span><span class="sxs-lookup"><span data-stu-id="266dd-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="266dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="266dd-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="266dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="266dd-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="266dd-106">[out]ICorDebugChain 物件，表示呼叫鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="266dd-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="266dd-107">如果這個鏈結自行呼叫 （如這個鏈結或偵錯工具初始化呼叫堆疊時，便會發生），`ppChain`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="266dd-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="266dd-108">備註</span><span class="sxs-lookup"><span data-stu-id="266dd-108">Remarks</span></span>  
 <span data-ttu-id="266dd-109">如果多個執行緒的呼叫已封送處理，可能是在不同的執行緒上呼叫鏈結。</span><span class="sxs-lookup"><span data-stu-id="266dd-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="266dd-110">需求</span><span class="sxs-lookup"><span data-stu-id="266dd-110">Requirements</span></span>  
 <span data-ttu-id="266dd-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="266dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="266dd-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="266dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="266dd-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="266dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="266dd-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="266dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
