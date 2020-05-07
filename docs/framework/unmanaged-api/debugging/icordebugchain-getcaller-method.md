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
ms.openlocfilehash: a6d26924773e6ad505975402ec3ace150d02cc3a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894620"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="81a68-102">ICorDebugChain::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="81a68-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="81a68-103">取得呼叫這個鏈的鏈。</span><span class="sxs-lookup"><span data-stu-id="81a68-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a68-104">語法</span><span class="sxs-lookup"><span data-stu-id="81a68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81a68-105">參數</span><span class="sxs-lookup"><span data-stu-id="81a68-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="81a68-106">脫銷代表呼叫鏈之 ICorDebugChain 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="81a68-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="81a68-107">如果這個鏈是自發呼叫的（如果這個鏈或偵錯工具已初始化呼叫堆疊， `ppChain`則會是 null）。</span><span class="sxs-lookup"><span data-stu-id="81a68-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81a68-108">備註</span><span class="sxs-lookup"><span data-stu-id="81a68-108">Remarks</span></span>  
 <span data-ttu-id="81a68-109">如果呼叫是線上程之間封送處理，則呼叫鏈可能會在不同的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="81a68-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a68-110">需求</span><span class="sxs-lookup"><span data-stu-id="81a68-110">Requirements</span></span>  
 <span data-ttu-id="81a68-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81a68-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a68-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81a68-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81a68-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81a68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81a68-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
