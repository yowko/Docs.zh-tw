---
title: ICorDebugChain::GetNext 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 47a90ed63ae217cb150f392ad9196f8d0d5764e3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894634"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="0150d-102">ICorDebugChain::GetNext 方法</span><span class="sxs-lookup"><span data-stu-id="0150d-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="0150d-103">取得執行緒的下一個框架鏈。</span><span class="sxs-lookup"><span data-stu-id="0150d-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0150d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0150d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0150d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0150d-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="0150d-106">脫銷ICorDebugChain 物件位址的指標，表示執行緒的下一個框架鏈。</span><span class="sxs-lookup"><span data-stu-id="0150d-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="0150d-107">如果這個鏈是最後一個鏈， `ppChain`則是 null。</span><span class="sxs-lookup"><span data-stu-id="0150d-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0150d-108">需求</span><span class="sxs-lookup"><span data-stu-id="0150d-108">Requirements</span></span>  
 <span data-ttu-id="0150d-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0150d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0150d-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0150d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0150d-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0150d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0150d-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0150d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
