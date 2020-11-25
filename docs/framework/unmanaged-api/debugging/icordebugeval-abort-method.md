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
ms.openlocfilehash: 6e6ea5e42c5e1b1943a080ae02e1dbf6d702bebc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705848"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="81d68-102">ICorDebugEval::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="81d68-102">ICorDebugEval::Abort Method</span></span>

<span data-ttu-id="81d68-103">中止這個 ICorDebugEval 物件目前正在執行的計算。</span><span class="sxs-lookup"><span data-stu-id="81d68-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d68-104">語法</span><span class="sxs-lookup"><span data-stu-id="81d68-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="81d68-105">備註</span><span class="sxs-lookup"><span data-stu-id="81d68-105">Remarks</span></span>  

 <span data-ttu-id="81d68-106">如果評估是嵌套的，而且不是最新的，則 `Abort` 方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="81d68-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d68-107">需求</span><span class="sxs-lookup"><span data-stu-id="81d68-107">Requirements</span></span>  

 <span data-ttu-id="81d68-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81d68-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d68-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81d68-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81d68-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81d68-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81d68-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d68-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
