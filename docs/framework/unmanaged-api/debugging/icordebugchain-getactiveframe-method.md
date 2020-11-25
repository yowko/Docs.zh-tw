---
title: ICorDebugChain::GetActiveFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: daecd216b4d7e9c23336b8956c13735549be901b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730132"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="e9017-102">ICorDebugChain::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="e9017-102">ICorDebugChain::GetActiveFrame Method</span></span>

<span data-ttu-id="e9017-103">取得使用中的 (，也就是鏈上最新的) 框架。</span><span class="sxs-lookup"><span data-stu-id="e9017-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9017-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9017-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9017-105">參數</span><span class="sxs-lookup"><span data-stu-id="e9017-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="e9017-106">擴展ICorDebugFrame 物件位址的指標，該物件表示目前的使用中 (，也就是最新的) 框架。</span><span class="sxs-lookup"><span data-stu-id="e9017-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9017-107">備註</span><span class="sxs-lookup"><span data-stu-id="e9017-107">Remarks</span></span>  

 <span data-ttu-id="e9017-108">如果沒有可用的受控堆疊框架， `ppFrame` 會設為 null。</span><span class="sxs-lookup"><span data-stu-id="e9017-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="e9017-109">如果使用中的框架無法使用，則呼叫會成功，而且 `ppFrame` 將會是 null。</span><span class="sxs-lookup"><span data-stu-id="e9017-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="e9017-110">使用中的框架將無法用於因為 CHAIN_ENTER_UNMANAGED 所起始的鏈，以及因 CHAIN_CLASS_INIT 而起始的部分鏈。</span><span class="sxs-lookup"><span data-stu-id="e9017-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="e9017-111">請參閱 CorDebugChainReason 列舉。</span><span class="sxs-lookup"><span data-stu-id="e9017-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9017-112">需求</span><span class="sxs-lookup"><span data-stu-id="e9017-112">Requirements</span></span>  

 <span data-ttu-id="e9017-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9017-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9017-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9017-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9017-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9017-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9017-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9017-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
