---
title: "ICorDebugFrame::GetChain 方法"
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
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 479ad2db4752f9e031783b430396286c6989b115
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="b1f77-102">ICorDebugFrame::GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="b1f77-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="b1f77-103">取得此框架就是鏈結的指標。</span><span class="sxs-lookup"><span data-stu-id="b1f77-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f77-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1f77-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1f77-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1f77-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="b1f77-106">[out]ICorDebugChain 物件，代表包含此框架鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="b1f77-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1f77-107">需求</span><span class="sxs-lookup"><span data-stu-id="b1f77-107">Requirements</span></span>  
 <span data-ttu-id="b1f77-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f77-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1f77-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1f77-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1f77-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1f77-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1f77-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1f77-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
