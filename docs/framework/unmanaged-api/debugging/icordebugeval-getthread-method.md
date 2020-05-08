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
ms.openlocfilehash: b985ada09e0e1914c5e60da61a45398fc6098b33
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976274"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="e0bde-102">ICorDebugEval::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="e0bde-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="e0bde-103">取得執行或將執行此評估的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e0bde-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bde-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0bde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0bde-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0bde-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="e0bde-106">脫銷代表執行緒之 ICorDebugThread 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e0bde-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0bde-107">需求</span><span class="sxs-lookup"><span data-stu-id="e0bde-107">Requirements</span></span>  
 <span data-ttu-id="e0bde-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0bde-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0bde-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0bde-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0bde-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0bde-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0bde-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0bde-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
