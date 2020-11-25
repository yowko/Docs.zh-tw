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
ms.openlocfilehash: e6b1d78b2bd95ea27f4b19a045cd2680342e8a80
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728091"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="6f1aa-102">ICorDebugThread::GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="6f1aa-102">ICorDebugThread::GetActiveChain Method</span></span>

<span data-ttu-id="6f1aa-103">取得這個 ICorDebugThread 物件上作用中 (最近) 堆疊鏈的介面指標。</span><span class="sxs-lookup"><span data-stu-id="6f1aa-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f1aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f1aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f1aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f1aa-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="6f1aa-106">擴展代表堆疊鏈之 ICorDebugChain 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="6f1aa-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f1aa-107">備註</span><span class="sxs-lookup"><span data-stu-id="6f1aa-107">Remarks</span></span>  

 <span data-ttu-id="6f1aa-108">`ppChain`如果沒有堆疊鏈目前為使用中，則參數為 null。</span><span class="sxs-lookup"><span data-stu-id="6f1aa-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f1aa-109">需求</span><span class="sxs-lookup"><span data-stu-id="6f1aa-109">Requirements</span></span>  

 <span data-ttu-id="6f1aa-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f1aa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f1aa-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f1aa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f1aa-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f1aa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f1aa-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f1aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
