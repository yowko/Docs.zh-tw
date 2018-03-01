---
title: "ICorDebugChain::GetNext 方法"
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
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd01e13c49ef2aa0f55b18e40c1763f61be09a57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="ab279-102">ICorDebugChain::GetNext 方法</span><span class="sxs-lookup"><span data-stu-id="ab279-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="ab279-103">取得執行緒中的下一個框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="ab279-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab279-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab279-104">Syntax</span></span>  
  
```  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab279-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab279-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="ab279-106">[out]ICorDebugChain 物件，表示下一個執行緒的框架鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="ab279-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="ab279-107">如果這個鏈結是最後一個鏈結`ppChain`為 null。</span><span class="sxs-lookup"><span data-stu-id="ab279-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab279-108">需求</span><span class="sxs-lookup"><span data-stu-id="ab279-108">Requirements</span></span>  
 <span data-ttu-id="ab279-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab279-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab279-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab279-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab279-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab279-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab279-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab279-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
