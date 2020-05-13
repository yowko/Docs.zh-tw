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
ms.openlocfilehash: 7da12554ba1db9a467aa03c01bfb3b584125b129
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213188"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="6e6b6-102">ICorDebugFunction2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="6e6b6-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="6e6b6-103">標示此 ICorDebugFunction2 所代表的函式，以 Just My Code 逐步執行。</span><span class="sxs-lookup"><span data-stu-id="6e6b6-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e6b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e6b6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e6b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e6b6-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="6e6b6-106">在設定為以將函式 `true` 標記為使用者程式碼，否則設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6e6b6-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="6e6b6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6e6b6-107">Return Values</span></span>  
  
|<span data-ttu-id="6e6b6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e6b6-108">HRESULT</span></span>|<span data-ttu-id="6e6b6-109">描述</span><span class="sxs-lookup"><span data-stu-id="6e6b6-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6e6b6-110">已成功標記函數。</span><span class="sxs-lookup"><span data-stu-id="6e6b6-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="6e6b6-111">無法將函式標記為使用者程式碼，因為它無法進行調試。</span><span class="sxs-lookup"><span data-stu-id="6e6b6-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e6b6-112">備註</span><span class="sxs-lookup"><span data-stu-id="6e6b6-112">Remarks</span></span>  
 <span data-ttu-id="6e6b6-113">Just My Code 的分檔器會略過非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e6b6-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="6e6b6-114">使用者程式碼必須是可偵錯工具代碼的子集。</span><span class="sxs-lookup"><span data-stu-id="6e6b6-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e6b6-115">需求</span><span class="sxs-lookup"><span data-stu-id="6e6b6-115">Requirements</span></span>  
 <span data-ttu-id="6e6b6-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e6b6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e6b6-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e6b6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e6b6-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e6b6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e6b6-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e6b6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
