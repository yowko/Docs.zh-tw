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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c79f3b3b976b83eb99f8aa26d38a1fe316de471a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744992"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="68f6c-102">ICorDebugChain::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="68f6c-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="68f6c-103">取得使用 (也就是最新) 鏈結上的框架。</span><span class="sxs-lookup"><span data-stu-id="68f6c-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f6c-104">語法</span><span class="sxs-lookup"><span data-stu-id="68f6c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f6c-105">參數</span><span class="sxs-lookup"><span data-stu-id="68f6c-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="68f6c-106">[out]ICorDebugFrame 物件，表示使用中位址的指標 (也就是最新) 鏈結上的框架。</span><span class="sxs-lookup"><span data-stu-id="68f6c-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68f6c-107">備註</span><span class="sxs-lookup"><span data-stu-id="68f6c-107">Remarks</span></span>  
 <span data-ttu-id="68f6c-108">如果任何受管理的堆疊框架，不可供使用，`ppFrame`設為 null。</span><span class="sxs-lookup"><span data-stu-id="68f6c-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="68f6c-109">如果找不到使用中畫面格，則呼叫會成功並`ppFrame`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="68f6c-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="68f6c-110">使用中框架將無法使用鏈結 CHAIN_ENTER_UNMANAGED，因為起始，並起始 CHAIN_CLASS_INIT 因為某些鏈結。</span><span class="sxs-lookup"><span data-stu-id="68f6c-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="68f6c-111">CorDebugChainReason 列舉，請參閱。</span><span class="sxs-lookup"><span data-stu-id="68f6c-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f6c-112">需求</span><span class="sxs-lookup"><span data-stu-id="68f6c-112">Requirements</span></span>  
 <span data-ttu-id="68f6c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68f6c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f6c-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68f6c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68f6c-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68f6c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68f6c-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f6c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
