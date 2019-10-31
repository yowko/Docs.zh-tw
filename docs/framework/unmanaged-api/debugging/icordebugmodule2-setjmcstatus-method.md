---
title: ICorDebugModule2::SetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129476"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="de206-102">ICorDebugModule2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="de206-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="de206-103">將此 ICorDebugModule2 中所有類別的所有方法的 Just My Code （JMC）狀態設定為指定的值，但在 `pTokens` 陣列中，它會設定為相反的值。</span><span class="sxs-lookup"><span data-stu-id="de206-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de206-104">語法</span><span class="sxs-lookup"><span data-stu-id="de206-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de206-105">參數</span><span class="sxs-lookup"><span data-stu-id="de206-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="de206-106">在如果要偵錯工具代碼，請設定為 `true`;否則，請將設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="de206-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="de206-107">[in] `pTokens` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="de206-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="de206-108">在`mdToken` 值的陣列，其中每一個都參考將其 JMC 狀態設定為的方法！`bIsJustMycode`。</span><span class="sxs-lookup"><span data-stu-id="de206-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de206-109">備註</span><span class="sxs-lookup"><span data-stu-id="de206-109">Remarks</span></span>  
 <span data-ttu-id="de206-110">`pTokens` 陣列中指定之每個方法的 JMC 狀態都會設定為與 `bIsJustMycode` 值相反的。</span><span class="sxs-lookup"><span data-stu-id="de206-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="de206-111">此模組中所有其他方法的狀態會設定為 `bIsJustMycode` 值。</span><span class="sxs-lookup"><span data-stu-id="de206-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="de206-112">`SetJMCStatus` 方法會清除此課程模組中所有先前的 JMC 設定。</span><span class="sxs-lookup"><span data-stu-id="de206-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="de206-113">如果已成功設定所有函數，`SetJMCStatus` 方法會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="de206-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="de206-114">如果某些已標記 `true` 的函式無法進行調試，它會傳回 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="de206-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de206-115">需求</span><span class="sxs-lookup"><span data-stu-id="de206-115">Requirements</span></span>  
 <span data-ttu-id="de206-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de206-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de206-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de206-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de206-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de206-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de206-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de206-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
