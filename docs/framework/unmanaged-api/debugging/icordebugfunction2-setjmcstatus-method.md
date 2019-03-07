---
title: ICorDebugFunction2::SetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49ced1b4be888c7550c3927d1b319ab2f0bef086
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501002"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="4238c-102">ICorDebugFunction2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="4238c-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="4238c-103">表示此 ICorDebugFunction2 Just My Code 的函式會將標示逐步執行。</span><span class="sxs-lookup"><span data-stu-id="4238c-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4238c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4238c-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4238c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4238c-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="4238c-106">[in]設定為`true`來標記的功能與使用者程式碼; 否則設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="4238c-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="4238c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4238c-107">Return Values</span></span>  
  
|<span data-ttu-id="4238c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4238c-108">HRESULT</span></span>|<span data-ttu-id="4238c-109">描述</span><span class="sxs-lookup"><span data-stu-id="4238c-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4238c-110">已成功地標示函式。</span><span class="sxs-lookup"><span data-stu-id="4238c-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="4238c-111">此函式無法標示為使用者程式碼，因為它不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="4238c-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4238c-112">備註</span><span class="sxs-lookup"><span data-stu-id="4238c-112">Remarks</span></span>  
 <span data-ttu-id="4238c-113">Just My Code 步進會略過的非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="4238c-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="4238c-114">使用者程式碼必須是可偵錯的程式碼的子集。</span><span class="sxs-lookup"><span data-stu-id="4238c-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4238c-115">需求</span><span class="sxs-lookup"><span data-stu-id="4238c-115">Requirements</span></span>  
 <span data-ttu-id="4238c-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4238c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4238c-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4238c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4238c-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4238c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4238c-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4238c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
