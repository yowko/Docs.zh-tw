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
ms.openlocfilehash: 326e170fa98c9e365f9b68bedb585f547ca207ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727701"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="d3225-102">ICorDebugChain::GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="d3225-102">ICorDebugChain::GetPrevious Method</span></span>

<span data-ttu-id="d3225-103">取得執行緒的上一鏈框架。</span><span class="sxs-lookup"><span data-stu-id="d3225-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3225-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3225-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3225-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3225-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="d3225-106">擴展ICorDebugChain 物件位址的指標，該物件代表此執行緒的前一鏈框架。</span><span class="sxs-lookup"><span data-stu-id="d3225-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="d3225-107">如果此鏈是第一個鏈， `ppChain` 則為 null。</span><span class="sxs-lookup"><span data-stu-id="d3225-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3225-108">需求</span><span class="sxs-lookup"><span data-stu-id="d3225-108">Requirements</span></span>  

 <span data-ttu-id="d3225-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3225-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3225-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3225-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3225-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3225-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3225-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3225-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
