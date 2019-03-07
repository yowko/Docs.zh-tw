---
title: ICorDebugEval::GetThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64cc5b6e7c6fe44080b35dc07f029ad311b88ca7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489380"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="6a768-102">ICorDebugEval::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="6a768-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="6a768-103">取得這項評估執行或即將執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="6a768-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a768-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a768-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a768-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a768-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="6a768-106">[out]ICorDebugThread 物件，表示執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="6a768-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a768-107">需求</span><span class="sxs-lookup"><span data-stu-id="6a768-107">Requirements</span></span>  
 <span data-ttu-id="6a768-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a768-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a768-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a768-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a768-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a768-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a768-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a768-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
