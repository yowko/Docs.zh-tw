---
title: ICorDebugChain::GetThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 291c8129a790c235ee6e7f163c49c4e1e726cce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402708"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="8a735-102">ICorDebugChain::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="8a735-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="8a735-103">取得實體的執行緒，這個呼叫鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="8a735-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a735-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a735-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a735-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a735-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="8a735-106">[out]ICorDebugThread 物件，表示在實體執行緒的指標此呼叫鏈結是的一部分。</span><span class="sxs-lookup"><span data-stu-id="8a735-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a735-107">需求</span><span class="sxs-lookup"><span data-stu-id="8a735-107">Requirements</span></span>  
 <span data-ttu-id="8a735-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a735-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a735-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a735-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a735-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a735-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a735-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a735-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
