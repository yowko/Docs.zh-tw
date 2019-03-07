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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fdcdf23dfee01e8bad1c95adb4de66f270d5e00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474965"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="060e4-102">ICorDebugChain::GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="060e4-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="060e4-103">取得執行緒先前的框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="060e4-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="060e4-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="060e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="060e4-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="060e4-106">[out]ICorDebugChain 物件，表示這個執行緒的畫面格的上一個鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="060e4-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="060e4-107">如果這個鏈結的第一個鏈結，`ppChain`為 null。</span><span class="sxs-lookup"><span data-stu-id="060e4-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="060e4-108">需求</span><span class="sxs-lookup"><span data-stu-id="060e4-108">Requirements</span></span>  
 <span data-ttu-id="060e4-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="060e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="060e4-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="060e4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="060e4-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="060e4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="060e4-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="060e4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
