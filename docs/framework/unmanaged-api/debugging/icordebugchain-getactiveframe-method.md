---
title: "ICorDebugChain::GetActiveFrame 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5de327c1579d05f6ae4a440fc76a3fb9ee99b13
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="98d27-102">ICorDebugChain::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="98d27-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="98d27-103">取得作用中 (也就是最新) 鏈結上的框架。</span><span class="sxs-lookup"><span data-stu-id="98d27-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d27-104">語法</span><span class="sxs-lookup"><span data-stu-id="98d27-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98d27-105">參數</span><span class="sxs-lookup"><span data-stu-id="98d27-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="98d27-106">[out]ICorDebugFrame 物件，表示使用中的位址指標 (也就是最新) 鏈結上的框架。</span><span class="sxs-lookup"><span data-stu-id="98d27-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98d27-107">備註</span><span class="sxs-lookup"><span data-stu-id="98d27-107">Remarks</span></span>  
 <span data-ttu-id="98d27-108">如果沒有受管理的堆疊框架，則`ppFrame`設為 null。</span><span class="sxs-lookup"><span data-stu-id="98d27-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="98d27-109">如果找不到使用中畫面格，則呼叫會成功並`ppFrame`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="98d27-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="98d27-110">使用中框架將會無法使用鏈結 CHAIN_ENTER_UNMANAGED，因為起始，因為 CHAIN_CLASS_INIT 起始部分鏈結。</span><span class="sxs-lookup"><span data-stu-id="98d27-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="98d27-111">請參閱 CorDebugChainReason 列舉。</span><span class="sxs-lookup"><span data-stu-id="98d27-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98d27-112">需求</span><span class="sxs-lookup"><span data-stu-id="98d27-112">Requirements</span></span>  
 <span data-ttu-id="98d27-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98d27-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d27-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98d27-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98d27-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98d27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98d27-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98d27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
