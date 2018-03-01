---
title: "ICorDebugChain::GetPrevious 方法"
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
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5f98395ff8e77aa52a470f893ea5db02d73fdf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="173f2-102">ICorDebugChain::GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="173f2-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="173f2-103">取得執行緒中先前的框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="173f2-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="173f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="173f2-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="173f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="173f2-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="173f2-106">[out]ICorDebugChain 物件，表示先前的這個執行緒的框架鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="173f2-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="173f2-107">如果這個鏈結是第一個鏈結`ppChain`為 null。</span><span class="sxs-lookup"><span data-stu-id="173f2-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="173f2-108">需求</span><span class="sxs-lookup"><span data-stu-id="173f2-108">Requirements</span></span>  
 <span data-ttu-id="173f2-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="173f2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="173f2-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="173f2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="173f2-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="173f2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="173f2-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="173f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
