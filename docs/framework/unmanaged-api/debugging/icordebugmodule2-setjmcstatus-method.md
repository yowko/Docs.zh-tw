---
title: "ICorDebugModule2::SetJMCStatus 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a461a9c05b18de45426247743c6e4ffca775025a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="c56f1-102">ICorDebugModule2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="c56f1-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="c56f1-103">設定的 Just My Code (JMC) 狀態的所有類別的所有方法和指定的值以外的這個 ICorDebugModule2`pTokens`陣列，它會設定為相反側的值。</span><span class="sxs-lookup"><span data-stu-id="c56f1-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c56f1-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c56f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="c56f1-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="c56f1-106">[in]設定為`true`程式碼是偵錯，否則如果設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="c56f1-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="c56f1-107">[in] `pTokens` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c56f1-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="c56f1-108">[in]陣列`mdToken`值，其中每個方法將會有其 JMC 狀態設定為所指的是 ！`bIsJustMycode`。</span><span class="sxs-lookup"><span data-stu-id="c56f1-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56f1-109">備註</span><span class="sxs-lookup"><span data-stu-id="c56f1-109">Remarks</span></span>  
 <span data-ttu-id="c56f1-110">每個方法中指定的 JMC 狀態`pTokens`陣列設相反`bIsJustMycode`值。</span><span class="sxs-lookup"><span data-stu-id="c56f1-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="c56f1-111">此模組中的其他所有方法的狀態設為`bIsJustMycode`值。</span><span class="sxs-lookup"><span data-stu-id="c56f1-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="c56f1-112">`SetJMCStatus`方法清除所有先前在此模組的 jmc 的方法設定。</span><span class="sxs-lookup"><span data-stu-id="c56f1-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="c56f1-113">`SetJMCStatus`方法會傳回 S_OK HRESULT，如果已成功設定所有函式。</span><span class="sxs-lookup"><span data-stu-id="c56f1-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="c56f1-114">它會傳回某些函式，如果 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT 標示`true`不是可偵錯。</span><span class="sxs-lookup"><span data-stu-id="c56f1-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c56f1-115">需求</span><span class="sxs-lookup"><span data-stu-id="c56f1-115">Requirements</span></span>  
 <span data-ttu-id="c56f1-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c56f1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c56f1-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c56f1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c56f1-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c56f1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c56f1-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c56f1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
