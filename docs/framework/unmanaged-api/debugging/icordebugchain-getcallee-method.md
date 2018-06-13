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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f050a3d9d37e43713c40896fb162bcf9932c6512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403366"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="e3f10-102">ICorDebugChain::GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="e3f10-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="e3f10-103">取得由這個鏈結所呼叫。</span><span class="sxs-lookup"><span data-stu-id="e3f10-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3f10-104">語法</span><span class="sxs-lookup"><span data-stu-id="e3f10-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3f10-105">參數</span><span class="sxs-lookup"><span data-stu-id="e3f10-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="e3f10-106">[out]ICorDebugChain 物件，表示呼叫的鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e3f10-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="e3f10-107">如果這個鏈結目前執行中 （也就是說，如果這個鏈結沒有在等待傳回呼叫的鏈結） 以及`ppChain`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="e3f10-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3f10-108">備註</span><span class="sxs-lookup"><span data-stu-id="e3f10-108">Remarks</span></span>  
 <span data-ttu-id="e3f10-109">這個鏈結將會等到前它會繼續執行，傳回呼叫的鏈結。</span><span class="sxs-lookup"><span data-stu-id="e3f10-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="e3f10-110">呼叫的鏈結可能會在跨執行緒封送處理呼叫的情況下的另一個執行緒上。</span><span class="sxs-lookup"><span data-stu-id="e3f10-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3f10-111">需求</span><span class="sxs-lookup"><span data-stu-id="e3f10-111">Requirements</span></span>  
 <span data-ttu-id="e3f10-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3f10-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3f10-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3f10-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3f10-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3f10-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3f10-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3f10-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
