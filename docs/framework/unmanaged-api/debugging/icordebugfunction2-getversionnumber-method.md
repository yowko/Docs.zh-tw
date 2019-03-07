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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497167"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="e0b24-102">ICorDebugFunction2::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="e0b24-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="e0b24-103">取得此函式的 編輯後繼續版本。</span><span class="sxs-lookup"><span data-stu-id="e0b24-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0b24-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0b24-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0b24-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0b24-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="e0b24-106">[out]此 ICorDebugFunction2 物件所代表的函式的版本號碼的整數指標。</span><span class="sxs-lookup"><span data-stu-id="e0b24-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0b24-107">備註</span><span class="sxs-lookup"><span data-stu-id="e0b24-107">Remarks</span></span>  
 <span data-ttu-id="e0b24-108">執行階段記錄的編輯已發生每個模組的偵錯工作階段的數目。</span><span class="sxs-lookup"><span data-stu-id="e0b24-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="e0b24-109">函式的版本號碼是其中一個超過編輯導入的函式的數目。</span><span class="sxs-lookup"><span data-stu-id="e0b24-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="e0b24-110">函式的原始版本是第 1 版。</span><span class="sxs-lookup"><span data-stu-id="e0b24-110">The function's original version is version 1.</span></span> <span data-ttu-id="e0b24-111">每次遞增的數字的模組[ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)該模組上呼叫。</span><span class="sxs-lookup"><span data-stu-id="e0b24-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="e0b24-112">因此，如果第一個和第三個呼叫中已取代的函式的主體`ICorDebugModule2::ApplyChanges`，`GetVersionNumber`可能會傳回版本 1、 2 或 4 個該函式，但不是第 3 版。</span><span class="sxs-lookup"><span data-stu-id="e0b24-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="e0b24-113">（該函式會有版本 3）。</span><span class="sxs-lookup"><span data-stu-id="e0b24-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="e0b24-114">版本號碼分別追蹤每個模組。</span><span class="sxs-lookup"><span data-stu-id="e0b24-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="e0b24-115">因此，如果您在模組 1 和模組 2 上未執行四個編輯，您模組 1 上的下一個編輯會將版本號碼為 6 模組 1 中的所有已編輯函式。</span><span class="sxs-lookup"><span data-stu-id="e0b24-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="e0b24-116">如果相同編輯涉及模組 2，模組 2 中的函式會取得版本數字 2。</span><span class="sxs-lookup"><span data-stu-id="e0b24-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="e0b24-117">取得版本號碼`GetVersionNumber`方法可能是藉由取得低於[icordebugfunction:: Getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e0b24-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="e0b24-118">[Icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法會執行相同的作業`ICorDebugFunction2::GetVersionNumber`。</span><span class="sxs-lookup"><span data-stu-id="e0b24-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0b24-119">需求</span><span class="sxs-lookup"><span data-stu-id="e0b24-119">Requirements</span></span>  
 <span data-ttu-id="e0b24-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0b24-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0b24-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0b24-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0b24-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0b24-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0b24-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0b24-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
