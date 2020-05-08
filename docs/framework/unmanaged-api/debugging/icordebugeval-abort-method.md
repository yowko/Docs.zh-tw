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
ms.openlocfilehash: 98a9b285323bc3ad94b4f555e72a4b3242519801
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976285"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="12d35-102">ICorDebugEval::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="12d35-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="12d35-103">中止此 ICorDebugEval 物件目前正在執行的計算。</span><span class="sxs-lookup"><span data-stu-id="12d35-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d35-104">語法</span><span class="sxs-lookup"><span data-stu-id="12d35-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="12d35-105">備註</span><span class="sxs-lookup"><span data-stu-id="12d35-105">Remarks</span></span>  
 <span data-ttu-id="12d35-106">如果評估是嵌套的，而且不是最新的，則`Abort`方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="12d35-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12d35-107">需求</span><span class="sxs-lookup"><span data-stu-id="12d35-107">Requirements</span></span>  
 <span data-ttu-id="12d35-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12d35-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12d35-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12d35-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12d35-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12d35-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12d35-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12d35-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
