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
ms.openlocfilehash: cfa6df7a812559f05a4c57381a5007c9c90238e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709644"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="56334-102">ICorDebugModule2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="56334-102">ICorDebugModule2::SetJMCStatus Method</span></span>

<span data-ttu-id="56334-103">將這個 ICorDebugModule2 中所有類別的所有方法的 Just My Code (JMC) 狀態設定為指定的值，但陣列中的值除外 `pTokens` ，其會設定為相反值。</span><span class="sxs-lookup"><span data-stu-id="56334-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56334-104">語法</span><span class="sxs-lookup"><span data-stu-id="56334-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56334-105">參數</span><span class="sxs-lookup"><span data-stu-id="56334-105">Parameters</span></span>  

 `bIsJustMycode`  
 <span data-ttu-id="56334-106">在 `true` 如果要偵錯工具代碼，請設定為，否則設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="56334-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="56334-107">[in] `pTokens` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="56334-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="56334-108">在值的陣列 `mdToken` ，每個值都會參考將其 JMC 狀態設為！的方法 `bIsJustMycode` 。</span><span class="sxs-lookup"><span data-stu-id="56334-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56334-109">備註</span><span class="sxs-lookup"><span data-stu-id="56334-109">Remarks</span></span>  

 <span data-ttu-id="56334-110">陣列中指定之每個方法的 JMC 狀態 `pTokens` 會設定為相對於 `bIsJustMycode` 該值的值。</span><span class="sxs-lookup"><span data-stu-id="56334-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="56334-111">此課程模組中所有其他方法的狀態都會設定為 `bIsJustMycode` 值。</span><span class="sxs-lookup"><span data-stu-id="56334-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="56334-112">`SetJMCStatus`此方法會清除此課程模組中所有先前的 JMC 設定。</span><span class="sxs-lookup"><span data-stu-id="56334-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="56334-113">`SetJMCStatus`如果已成功設定所有函數，方法會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="56334-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="56334-114">如果某些標記的函式無法進行調試，它會傳回 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT `true` 。</span><span class="sxs-lookup"><span data-stu-id="56334-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56334-115">需求</span><span class="sxs-lookup"><span data-stu-id="56334-115">Requirements</span></span>  

 <span data-ttu-id="56334-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56334-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56334-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56334-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56334-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56334-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56334-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56334-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
