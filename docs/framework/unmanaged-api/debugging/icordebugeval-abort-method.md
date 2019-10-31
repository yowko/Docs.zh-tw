---
title: ICorDebugEval::Abort 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: 78402e5e099815fe309618e692285de91b8b29f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124244"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="8bb58-102">ICorDebugEval::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="8bb58-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="8bb58-103">中止此 ICorDebugEval 物件目前正在執行的計算。</span><span class="sxs-lookup"><span data-stu-id="8bb58-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb58-104">語法</span><span class="sxs-lookup"><span data-stu-id="8bb58-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8bb58-105">備註</span><span class="sxs-lookup"><span data-stu-id="8bb58-105">Remarks</span></span>  
 <span data-ttu-id="8bb58-106">如果評估是嵌套的，而且不是最新的，則 `Abort` 方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="8bb58-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bb58-107">需求</span><span class="sxs-lookup"><span data-stu-id="8bb58-107">Requirements</span></span>  
 <span data-ttu-id="8bb58-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8bb58-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bb58-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bb58-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bb58-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bb58-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bb58-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bb58-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
