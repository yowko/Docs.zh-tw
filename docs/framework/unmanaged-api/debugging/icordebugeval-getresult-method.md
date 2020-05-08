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
ms.openlocfilehash: 2d065d956319076d3b92eddafd4a2c25ffbfbac1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976261"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="48f4e-102">ICorDebugEval::GetResult 方法</span><span class="sxs-lookup"><span data-stu-id="48f4e-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="48f4e-103">取得此評估的結果。</span><span class="sxs-lookup"><span data-stu-id="48f4e-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="48f4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48f4e-105">參數</span><span class="sxs-lookup"><span data-stu-id="48f4e-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="48f4e-106">脫銷ICorDebugValue 物件位址的指標，如果評估正常完成，表示此評估的結果。</span><span class="sxs-lookup"><span data-stu-id="48f4e-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48f4e-107">備註</span><span class="sxs-lookup"><span data-stu-id="48f4e-107">Remarks</span></span>  
 <span data-ttu-id="48f4e-108">只有`GetResult`在評估完成後，方法才有效。</span><span class="sxs-lookup"><span data-stu-id="48f4e-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="48f4e-109">如果評估正常完成， `ppResult`會指定結果。</span><span class="sxs-lookup"><span data-stu-id="48f4e-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="48f4e-110">如果它以例外狀況結束，則結果會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="48f4e-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="48f4e-111">如果是新物件的評估，則結果會是新物件的參考。</span><span class="sxs-lookup"><span data-stu-id="48f4e-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f4e-112">需求</span><span class="sxs-lookup"><span data-stu-id="48f4e-112">Requirements</span></span>  
 <span data-ttu-id="48f4e-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48f4e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f4e-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48f4e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48f4e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48f4e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48f4e-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48f4e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
