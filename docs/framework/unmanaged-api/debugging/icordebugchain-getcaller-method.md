---
title: ICorDebugChain::GetCaller 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 5a07550d44857526e8ab4ded9f1827ef12e3bba4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192142"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="2fd61-102">ICorDebugChain::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="2fd61-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="2fd61-103">取得呼叫這個鏈的鏈。</span><span class="sxs-lookup"><span data-stu-id="2fd61-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd61-104">語法</span><span class="sxs-lookup"><span data-stu-id="2fd61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fd61-105">參數</span><span class="sxs-lookup"><span data-stu-id="2fd61-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="2fd61-106">脫銷代表呼叫鏈之 ICorDebugChain 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="2fd61-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="2fd61-107">如果這個鏈是自發呼叫的（例如，如果這個鏈或偵錯工具已初始化呼叫堆疊），`ppChain` 將會是 null。</span><span class="sxs-lookup"><span data-stu-id="2fd61-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fd61-108">備註</span><span class="sxs-lookup"><span data-stu-id="2fd61-108">Remarks</span></span>  
 <span data-ttu-id="2fd61-109">如果呼叫是線上程之間封送處理，則呼叫鏈可能會在不同的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="2fd61-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd61-110">需求</span><span class="sxs-lookup"><span data-stu-id="2fd61-110">Requirements</span></span>  
 <span data-ttu-id="2fd61-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2fd61-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd61-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fd61-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fd61-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fd61-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd61-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd61-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
