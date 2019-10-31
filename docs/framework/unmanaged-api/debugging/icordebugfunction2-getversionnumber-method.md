---
title: ICorDebugFunction2::GetVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 5826297d8151cf05e1ec08acbf5c9cd381d2452b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137797"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="6a9cd-102">ICorDebugFunction2::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="6a9cd-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="6a9cd-103">取得此函式的編輯後繼續版本。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a9cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a9cd-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a9cd-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="6a9cd-106">脫銷整數的指標，這是這個 ICorDebugFunction2 物件所表示之函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9cd-107">備註</span><span class="sxs-lookup"><span data-stu-id="6a9cd-107">Remarks</span></span>  
 <span data-ttu-id="6a9cd-108">執行時間會持續追蹤在「偵錯工具」會話期間，每個模組所進行的編輯次數。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="6a9cd-109">函式的版本號碼比引進函數的編輯次數還要多。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="6a9cd-110">函式的原始版本為第1版。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-110">The function's original version is version 1.</span></span> <span data-ttu-id="6a9cd-111">每次在該模組上呼叫[ICorDebugModule2：： ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)時，模組的數目就會遞增。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="6a9cd-112">因此，如果第一個和第三個呼叫中已取代函式的主體 `ICorDebugModule2::ApplyChanges`，`GetVersionNumber` 可能會傳回該函式的版本1、2或4，但不會傳回第3版。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="6a9cd-113">（該函數不會有第3版）。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="6a9cd-114">針對每個模組分別追蹤版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="6a9cd-115">因此，如果您在模組1上執行四項編輯，而在模組2上執行了 [無]，則下一次編輯模組1將會為模組1中所有編輯的函式指派6的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="6a9cd-116">如果相同的編輯觸及模組2，則模組2中的函式會取得版本號碼2。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="6a9cd-117">`GetVersionNumber` 方法所取得的版本號碼可能低於[ICorDebugFunction：： GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)所取得的版本編號。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="6a9cd-118">[ICorDebugCode：： GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法會執行與 `ICorDebugFunction2::GetVersionNumber`相同的作業。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9cd-119">需求</span><span class="sxs-lookup"><span data-stu-id="6a9cd-119">Requirements</span></span>  
 <span data-ttu-id="6a9cd-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a9cd-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9cd-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a9cd-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a9cd-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9cd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a9cd-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a9cd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
