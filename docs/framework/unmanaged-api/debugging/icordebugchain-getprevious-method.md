---
title: "ICorDebugChain::GetPrevious 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetPrevious
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1203aa4a6e35574c1d026ddc05cac810fed5b78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="541f7-102">ICorDebugChain::GetPrevious 方法</span><span class="sxs-lookup"><span data-stu-id="541f7-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="541f7-103">取得執行緒中先前的框架鏈結。</span><span class="sxs-lookup"><span data-stu-id="541f7-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="541f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="541f7-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="541f7-105">參數</span><span class="sxs-lookup"><span data-stu-id="541f7-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="541f7-106">[out]ICorDebugChain 物件，表示先前的這個執行緒的框架鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="541f7-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="541f7-107">如果這個鏈結是第一個鏈結`ppChain`為 null。</span><span class="sxs-lookup"><span data-stu-id="541f7-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="541f7-108">需求</span><span class="sxs-lookup"><span data-stu-id="541f7-108">Requirements</span></span>  
 <span data-ttu-id="541f7-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="541f7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="541f7-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="541f7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="541f7-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="541f7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="541f7-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="541f7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
