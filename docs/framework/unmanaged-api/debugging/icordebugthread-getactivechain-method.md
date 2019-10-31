---
title: ICorDebugThread::GetActiveChain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: 99a617ef21ee3c3319b1ebe7d3ab8367659b6ef8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133548"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="252c2-102">ICorDebugThread::GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="252c2-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="252c2-103">取得此 ICorDebugThread 物件上作用中（最新）堆疊鏈的介面指標。</span><span class="sxs-lookup"><span data-stu-id="252c2-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="252c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="252c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="252c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="252c2-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="252c2-106">脫銷代表堆疊鏈之 ICorDebugChain 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="252c2-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="252c2-107">備註</span><span class="sxs-lookup"><span data-stu-id="252c2-107">Remarks</span></span>  
 <span data-ttu-id="252c2-108">如果目前沒有作用中的堆疊鏈，則 `ppChain` 參數為 null。</span><span class="sxs-lookup"><span data-stu-id="252c2-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="252c2-109">需求</span><span class="sxs-lookup"><span data-stu-id="252c2-109">Requirements</span></span>  
 <span data-ttu-id="252c2-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="252c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="252c2-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="252c2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="252c2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="252c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="252c2-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="252c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
