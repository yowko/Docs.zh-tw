---
title: ICorDebugEval::IsActive 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
ms.openlocfilehash: bd10af53d7803964ed6e699ce5328aa8a860216c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085026"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="e9bb6-102">ICorDebugEval::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="e9bb6-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="e9bb6-103">取得值，指出這個 ICorDebugEval 物件目前是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="e9bb6-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9bb6-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9bb6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9bb6-105">參數</span><span class="sxs-lookup"><span data-stu-id="e9bb6-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="e9bb6-106">脫銷指出此評估是否作用中的值指標。</span><span class="sxs-lookup"><span data-stu-id="e9bb6-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9bb6-107">需求</span><span class="sxs-lookup"><span data-stu-id="e9bb6-107">Requirements</span></span>  
 <span data-ttu-id="e9bb6-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9bb6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9bb6-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9bb6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9bb6-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9bb6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9bb6-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9bb6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
