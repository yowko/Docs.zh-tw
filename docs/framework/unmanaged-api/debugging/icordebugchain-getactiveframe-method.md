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
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894673"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="44346-102">ICorDebugChain::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="44346-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="44346-103">取得鏈上的現用（也就是最新的）框架。</span><span class="sxs-lookup"><span data-stu-id="44346-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44346-104">語法</span><span class="sxs-lookup"><span data-stu-id="44346-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44346-105">參數</span><span class="sxs-lookup"><span data-stu-id="44346-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="44346-106">脫銷ICorDebugFrame 物件位址的指標，表示鏈上的現用（也就是最新的）框架。</span><span class="sxs-lookup"><span data-stu-id="44346-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44346-107">備註</span><span class="sxs-lookup"><span data-stu-id="44346-107">Remarks</span></span>  
 <span data-ttu-id="44346-108">如果沒有可用的受控堆疊框架， `ppFrame`則會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="44346-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="44346-109">如果作用中的框架無法使用，呼叫將會成功， `ppFrame`而且將會是 null。</span><span class="sxs-lookup"><span data-stu-id="44346-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="44346-110">由於 CHAIN_ENTER_UNMANAGED，以及因為 CHAIN_CLASS_INIT 而起始的部分鏈，使用中的框架將無法用於起始鏈。</span><span class="sxs-lookup"><span data-stu-id="44346-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="44346-111">請參閱 CorDebugChainReason 列舉。</span><span class="sxs-lookup"><span data-stu-id="44346-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44346-112">需求</span><span class="sxs-lookup"><span data-stu-id="44346-112">Requirements</span></span>  
 <span data-ttu-id="44346-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44346-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44346-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44346-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44346-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44346-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44346-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44346-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
