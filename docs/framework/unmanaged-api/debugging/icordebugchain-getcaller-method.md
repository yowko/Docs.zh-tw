---
title: ICorDebugChain::GetCaller 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd65de77209f5a981c0a4c291f8573a61cf6335b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489549"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="0230d-102">ICorDebugChain::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="0230d-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="0230d-103">取得呼叫這個接收鏈結的鏈結。</span><span class="sxs-lookup"><span data-stu-id="0230d-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0230d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0230d-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0230d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0230d-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="0230d-106">[out]ICorDebugChain 物件，表示呼叫鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="0230d-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="0230d-107">如果這個鏈結會呼叫 （如這個鏈結或偵錯工具初始化呼叫堆疊時，會發生這個狀況），`ppChain`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="0230d-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0230d-108">備註</span><span class="sxs-lookup"><span data-stu-id="0230d-108">Remarks</span></span>  
 <span data-ttu-id="0230d-109">如果跨執行緒封送處理呼叫，可能會在不同的執行緒，會呼叫鏈結。</span><span class="sxs-lookup"><span data-stu-id="0230d-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0230d-110">需求</span><span class="sxs-lookup"><span data-stu-id="0230d-110">Requirements</span></span>  
 <span data-ttu-id="0230d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0230d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0230d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0230d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0230d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0230d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0230d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0230d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
