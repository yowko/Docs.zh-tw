---
title: "ICorDebugFunction2::GetVersionNumber 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.GetVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37b9e34174d88be08c92c54906ebd20977dc266a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="f7d63-102">ICorDebugFunction2::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="f7d63-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="f7d63-103">取得此函式的編輯後繼續版本。</span><span class="sxs-lookup"><span data-stu-id="f7d63-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d63-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7d63-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7d63-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7d63-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="f7d63-106">[out]此 ICorDebugFunction2 物件所代表的函式的版本號碼的整數指標。</span><span class="sxs-lookup"><span data-stu-id="f7d63-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7d63-107">備註</span><span class="sxs-lookup"><span data-stu-id="f7d63-107">Remarks</span></span>  
 <span data-ttu-id="f7d63-108">執行階段記錄的數目已發生每個模組的偵錯工作階段期間的編輯。</span><span class="sxs-lookup"><span data-stu-id="f7d63-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="f7d63-109">函式的版本號碼是其中一個超過編輯導入函式的數目。</span><span class="sxs-lookup"><span data-stu-id="f7d63-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="f7d63-110">函式的原始版本為第 1 版。</span><span class="sxs-lookup"><span data-stu-id="f7d63-110">The function's original version is version 1.</span></span> <span data-ttu-id="f7d63-111">數字遞增模組，每次[icordebugmodule2:: Applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)該模組上呼叫。</span><span class="sxs-lookup"><span data-stu-id="f7d63-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="f7d63-112">因此，如果第一個和第三個呼叫中被取代的函式主體`ICorDebugModule2::ApplyChanges`，`GetVersionNumber`可能會傳回版本 1、 2 或 4，該函式，但不是第 3 版。</span><span class="sxs-lookup"><span data-stu-id="f7d63-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="f7d63-113">（該函式會有版本 3）。</span><span class="sxs-lookup"><span data-stu-id="f7d63-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="f7d63-114">版本號碼是個別追蹤每個模組。</span><span class="sxs-lookup"><span data-stu-id="f7d63-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="f7d63-115">因此，如果您對模組 1 和無模組 2 上執行四個的編輯，您的下一個編輯模組 1 上指派版本號碼為 6 模組 1 中編輯過的函式。</span><span class="sxs-lookup"><span data-stu-id="f7d63-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="f7d63-116">如果相同編輯涉及模組 2，模組 2 中的函式會為 2 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f7d63-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="f7d63-117">取得版本號碼`GetVersionNumber`方法可能會低於取得[icordebugfunction:: Getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d63-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="f7d63-118">[Icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法會執行相同操作，因為`ICorDebugFunction2::GetVersionNumber`。</span><span class="sxs-lookup"><span data-stu-id="f7d63-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d63-119">需求</span><span class="sxs-lookup"><span data-stu-id="f7d63-119">Requirements</span></span>  
 <span data-ttu-id="f7d63-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d63-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d63-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7d63-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7d63-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7d63-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7d63-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d63-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
