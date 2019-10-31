---
title: ICorDebugChain::GetPrevious 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: c7598a9d93631ca93187886fd8929ba10726dad7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124728"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="68116-102">ICorDebugChain::GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="68116-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="68116-103">取得執行緒的先前框架鏈。</span><span class="sxs-lookup"><span data-stu-id="68116-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68116-104">語法</span><span class="sxs-lookup"><span data-stu-id="68116-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68116-105">參數</span><span class="sxs-lookup"><span data-stu-id="68116-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="68116-106">脫銷ICorDebugChain 物件位址的指標，表示此執行緒先前的框架鏈。</span><span class="sxs-lookup"><span data-stu-id="68116-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="68116-107">如果這個鏈是第一個鏈，`ppChain` 是 null。</span><span class="sxs-lookup"><span data-stu-id="68116-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68116-108">需求</span><span class="sxs-lookup"><span data-stu-id="68116-108">Requirements</span></span>  
 <span data-ttu-id="68116-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68116-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68116-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68116-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68116-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68116-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68116-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68116-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
