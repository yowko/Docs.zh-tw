---
title: ICorDebugChain::GetCallee 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: a28da34cd3080826f346b8957aa6ba38258b924f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730119"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="0585c-102">ICorDebugChain::GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="0585c-102">ICorDebugChain::GetCallee Method</span></span>

<span data-ttu-id="0585c-103">取得此鏈所呼叫的鏈。</span><span class="sxs-lookup"><span data-stu-id="0585c-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0585c-104">語法</span><span class="sxs-lookup"><span data-stu-id="0585c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0585c-105">參數</span><span class="sxs-lookup"><span data-stu-id="0585c-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="0585c-106">擴展ICorDebugChain 物件位址的指標，該物件表示呼叫的鏈。</span><span class="sxs-lookup"><span data-stu-id="0585c-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="0585c-107">如果此鏈目前正在執行 (也就是，如果此鏈未等候被呼叫的鏈傳回) ， `ppChain` 將會是 null。</span><span class="sxs-lookup"><span data-stu-id="0585c-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0585c-108">備註</span><span class="sxs-lookup"><span data-stu-id="0585c-108">Remarks</span></span>  

 <span data-ttu-id="0585c-109">在繼續執行之前，此鏈會等候被呼叫的鏈返回。</span><span class="sxs-lookup"><span data-stu-id="0585c-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="0585c-110">在跨執行緒封送呼叫的情況下，呼叫的鏈可能會在另一個執行緒上。</span><span class="sxs-lookup"><span data-stu-id="0585c-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0585c-111">需求</span><span class="sxs-lookup"><span data-stu-id="0585c-111">Requirements</span></span>  

 <span data-ttu-id="0585c-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0585c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0585c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0585c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0585c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0585c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0585c-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0585c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
