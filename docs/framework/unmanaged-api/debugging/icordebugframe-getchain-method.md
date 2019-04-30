---
title: ICorDebugFrame::GetChain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 032c1e3dcfe50cd30953ca581ff9f0d83b78518d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995861"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="36910-102">ICorDebugFrame::GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="36910-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="36910-103">取得此範圍是一部分的鏈結的指標。</span><span class="sxs-lookup"><span data-stu-id="36910-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36910-104">語法</span><span class="sxs-lookup"><span data-stu-id="36910-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36910-105">參數</span><span class="sxs-lookup"><span data-stu-id="36910-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="36910-106">[out]ICorDebugChain 物件，表示包含此框架鏈結的位址指標。</span><span class="sxs-lookup"><span data-stu-id="36910-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36910-107">需求</span><span class="sxs-lookup"><span data-stu-id="36910-107">Requirements</span></span>  
 <span data-ttu-id="36910-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36910-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36910-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36910-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36910-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36910-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36910-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36910-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
