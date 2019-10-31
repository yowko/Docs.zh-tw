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
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137787"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="c0307-102">ICorDebugFunction2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="c0307-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="c0307-103">標示此 ICorDebugFunction2 所代表的函式，以 Just My Code 逐步執行。</span><span class="sxs-lookup"><span data-stu-id="c0307-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0307-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0307-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0307-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0307-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="c0307-106">在設定為 `true` 以將函式標記為使用者程式碼;否則，請將設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c0307-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="c0307-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c0307-107">Return Values</span></span>  
  
|<span data-ttu-id="c0307-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0307-108">HRESULT</span></span>|<span data-ttu-id="c0307-109">描述</span><span class="sxs-lookup"><span data-stu-id="c0307-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c0307-110">已成功標記函數。</span><span class="sxs-lookup"><span data-stu-id="c0307-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="c0307-111">無法將函式標記為使用者程式碼，因為它無法進行調試。</span><span class="sxs-lookup"><span data-stu-id="c0307-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0307-112">備註</span><span class="sxs-lookup"><span data-stu-id="c0307-112">Remarks</span></span>  
 <span data-ttu-id="c0307-113">Just My Code 的分檔器會略過非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0307-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="c0307-114">使用者程式碼必須是可偵錯工具代碼的子集。</span><span class="sxs-lookup"><span data-stu-id="c0307-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0307-115">需求</span><span class="sxs-lookup"><span data-stu-id="c0307-115">Requirements</span></span>  
 <span data-ttu-id="c0307-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0307-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0307-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0307-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0307-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0307-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0307-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0307-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
