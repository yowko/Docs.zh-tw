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
ms.openlocfilehash: d5109043a8601d7997f52e88ea472644f1b9ca03
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208742"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="c7848-102">ICorDebugModule2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="c7848-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="c7848-103">將此 ICorDebugModule2 中所有類別的所有方法的 Just My Code （JMC）狀態設定為指定的值，但陣列中的所有類別都 `pTokens` 設定為相反的值。</span><span class="sxs-lookup"><span data-stu-id="c7848-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7848-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7848-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7848-105">參數</span><span class="sxs-lookup"><span data-stu-id="c7848-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="c7848-106">在`true`如果要偵錯工具代碼，則設定為，否則設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c7848-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="c7848-107">[in] `pTokens` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c7848-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="c7848-108">在值的陣列 `mdToken` ，其中每一個都會參考將其 JMC 狀態設定為！的方法 `bIsJustMycode` 。</span><span class="sxs-lookup"><span data-stu-id="c7848-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7848-109">備註</span><span class="sxs-lookup"><span data-stu-id="c7848-109">Remarks</span></span>  
 <span data-ttu-id="c7848-110">陣列中指定之每個方法的 JMC 狀態 `pTokens` 會設定為與值相反的 `bIsJustMycode` 。</span><span class="sxs-lookup"><span data-stu-id="c7848-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="c7848-111">此模組中所有其他方法的狀態會設定為 `bIsJustMycode` 值。</span><span class="sxs-lookup"><span data-stu-id="c7848-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="c7848-112">`SetJMCStatus`方法會清除此課程模組中所有先前的 JMC 設定。</span><span class="sxs-lookup"><span data-stu-id="c7848-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="c7848-113">`SetJMCStatus`如果已成功設定所有函式，此方法會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="c7848-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="c7848-114">如果某些標記的函式無法進行可調試，它會傳回 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT `true` 。</span><span class="sxs-lookup"><span data-stu-id="c7848-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7848-115">需求</span><span class="sxs-lookup"><span data-stu-id="c7848-115">Requirements</span></span>  
 <span data-ttu-id="c7848-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7848-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7848-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7848-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7848-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7848-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7848-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7848-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
