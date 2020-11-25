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
ms.openlocfilehash: 55f219b5b834f365b87440e69bfa7d2c4e519235
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696085"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="7b439-102">ICorDebugFunction2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="7b439-102">ICorDebugFunction2::SetJMCStatus Method</span></span>

<span data-ttu-id="7b439-103">針對 Just My Code 逐步執行，標記此 ICorDebugFunction2 所代表的函式。</span><span class="sxs-lookup"><span data-stu-id="7b439-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b439-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b439-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b439-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b439-105">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="7b439-106">在若設定為，則會將函式 `true` 標示為使用者程式碼; 否則，請將設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7b439-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="7b439-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7b439-107">Return Values</span></span>  
  
|<span data-ttu-id="7b439-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b439-108">HRESULT</span></span>|<span data-ttu-id="7b439-109">描述</span><span class="sxs-lookup"><span data-stu-id="7b439-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7b439-110">已成功標示函數。</span><span class="sxs-lookup"><span data-stu-id="7b439-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="7b439-111">因為無法進行調試，所以無法將函式標示為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b439-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b439-112">備註</span><span class="sxs-lookup"><span data-stu-id="7b439-112">Remarks</span></span>  

 <span data-ttu-id="7b439-113">Just My Code 的分檔器將會略過非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b439-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="7b439-114">使用者程式碼必須是可偵錯工具代碼的子集。</span><span class="sxs-lookup"><span data-stu-id="7b439-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b439-115">需求</span><span class="sxs-lookup"><span data-stu-id="7b439-115">Requirements</span></span>  

 <span data-ttu-id="7b439-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b439-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b439-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b439-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b439-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b439-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b439-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b439-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
