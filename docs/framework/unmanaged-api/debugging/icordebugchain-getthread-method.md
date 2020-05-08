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
ms.openlocfilehash: 28b54026c8743f31a420e164944f60709e2e271b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894362"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="c3a37-102">ICorDebugChain::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="c3a37-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="c3a37-103">取得此呼叫鏈所屬的實體執行緒。</span><span class="sxs-lookup"><span data-stu-id="c3a37-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a37-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3a37-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3a37-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3a37-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="c3a37-106">脫銷ICorDebugThread 物件的指標，表示此呼叫鏈所屬的實體執行緒。</span><span class="sxs-lookup"><span data-stu-id="c3a37-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a37-107">需求</span><span class="sxs-lookup"><span data-stu-id="c3a37-107">Requirements</span></span>  
 <span data-ttu-id="c3a37-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a37-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a37-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3a37-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3a37-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3a37-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3a37-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a37-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
