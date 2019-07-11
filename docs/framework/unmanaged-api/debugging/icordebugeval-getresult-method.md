---
title: ICorDebugEval::GetResult 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b12ba5ad5c85643d1f4c91585cf7abca210d22bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752935"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="e59e9-102">ICorDebugEval::GetResult 方法</span><span class="sxs-lookup"><span data-stu-id="e59e9-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="e59e9-103">取得這項評估的結果。</span><span class="sxs-lookup"><span data-stu-id="e59e9-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e59e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e59e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e59e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="e59e9-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="e59e9-106">[out]ICorDebugValue 物件，表示這項評估的結果，如果評估正常完成的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e59e9-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e59e9-107">備註</span><span class="sxs-lookup"><span data-stu-id="e59e9-107">Remarks</span></span>  
 <span data-ttu-id="e59e9-108">`GetResult`方法在完成評估之後，才是有效。</span><span class="sxs-lookup"><span data-stu-id="e59e9-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="e59e9-109">如果評估一般來說，完成`ppResult`指定的結果。</span><span class="sxs-lookup"><span data-stu-id="e59e9-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="e59e9-110">如果它終止的例外狀況，則結果會是擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e59e9-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="e59e9-111">如果評估為新的物件，則結果會是新物件的參考。</span><span class="sxs-lookup"><span data-stu-id="e59e9-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e59e9-112">需求</span><span class="sxs-lookup"><span data-stu-id="e59e9-112">Requirements</span></span>  
 <span data-ttu-id="e59e9-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e59e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e59e9-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e59e9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e59e9-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e59e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e59e9-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e59e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
