---
title: "ICorDebugFunction2::SetJMCStatus 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ecbcd5b8171a169fbfdd7175d3d9dfbbcb3855f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="f1b81-102">ICorDebugFunction2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="f1b81-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="f1b81-103">標示函式，由這個 ICorDebugFunction2 代表 Just My Code 逐步執行。</span><span class="sxs-lookup"><span data-stu-id="f1b81-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b81-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1b81-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1b81-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1b81-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="f1b81-106">[in]設定為`true`標示標示為使用者程式碼; 否則設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="f1b81-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="f1b81-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1b81-107">Return Values</span></span>  
  
|<span data-ttu-id="f1b81-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1b81-108">HRESULT</span></span>|<span data-ttu-id="f1b81-109">說明</span><span class="sxs-lookup"><span data-stu-id="f1b81-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f1b81-110">已成功地標示函式。</span><span class="sxs-lookup"><span data-stu-id="f1b81-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="f1b81-111">函式不被標記為使用者程式碼，因為它無法偵錯。</span><span class="sxs-lookup"><span data-stu-id="f1b81-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1b81-112">備註</span><span class="sxs-lookup"><span data-stu-id="f1b81-112">Remarks</span></span>  
 <span data-ttu-id="f1b81-113">Just My Code stepper 將略過的非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1b81-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="f1b81-114">使用者程式碼必須是可偵錯的程式碼的子集。</span><span class="sxs-lookup"><span data-stu-id="f1b81-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1b81-115">需求</span><span class="sxs-lookup"><span data-stu-id="f1b81-115">Requirements</span></span>  
 <span data-ttu-id="f1b81-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1b81-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1b81-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1b81-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1b81-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1b81-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1b81-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1b81-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
