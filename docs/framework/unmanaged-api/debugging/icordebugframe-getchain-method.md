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
ms.openlocfilehash: 9677fd14f50cf93eac7eeaef784082d45e8884c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137679"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="090f8-102">ICorDebugFrame::GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="090f8-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="090f8-103">取得此框架所屬之鏈的指標。</span><span class="sxs-lookup"><span data-stu-id="090f8-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="090f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="090f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="090f8-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="090f8-106">脫銷ICorDebugChain 物件位址的指標，表示包含此框架的鏈。</span><span class="sxs-lookup"><span data-stu-id="090f8-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="090f8-107">需求</span><span class="sxs-lookup"><span data-stu-id="090f8-107">Requirements</span></span>  
 <span data-ttu-id="090f8-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="090f8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="090f8-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="090f8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="090f8-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="090f8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="090f8-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="090f8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
