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
ms.openlocfilehash: 70e79378ad8eb2599199a1f7bc57cf530c9b4dd3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379686"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="f456b-102">ICorDebugThread::GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="f456b-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="f456b-103">取得此 ICorDebugThread 物件上作用中（最新）堆疊鏈的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f456b-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f456b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f456b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f456b-105">參數</span><span class="sxs-lookup"><span data-stu-id="f456b-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="f456b-106">脫銷代表堆疊鏈之 ICorDebugChain 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="f456b-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f456b-107">備註</span><span class="sxs-lookup"><span data-stu-id="f456b-107">Remarks</span></span>  
 <span data-ttu-id="f456b-108">`ppChain`如果堆疊鏈目前不在作用中，則參數為 null。</span><span class="sxs-lookup"><span data-stu-id="f456b-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f456b-109">需求</span><span class="sxs-lookup"><span data-stu-id="f456b-109">Requirements</span></span>  
 <span data-ttu-id="f456b-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f456b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f456b-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f456b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f456b-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f456b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f456b-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f456b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
