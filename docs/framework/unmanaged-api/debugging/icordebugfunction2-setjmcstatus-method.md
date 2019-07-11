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
ms.openlocfilehash: 67959b2ebbfb62b47a1b2a770e278d043fc66d21
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754926"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="5e098-102">ICorDebugFunction2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="5e098-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="5e098-103">表示此 ICorDebugFunction2 Just My Code 的函式會將標示逐步執行。</span><span class="sxs-lookup"><span data-stu-id="5e098-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e098-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e098-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e098-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e098-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="5e098-106">[in]設定為`true`來標記的功能與使用者程式碼; 否則設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="5e098-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="5e098-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e098-107">Return Values</span></span>  
  
|<span data-ttu-id="5e098-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e098-108">HRESULT</span></span>|<span data-ttu-id="5e098-109">描述</span><span class="sxs-lookup"><span data-stu-id="5e098-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5e098-110">已成功地標示函式。</span><span class="sxs-lookup"><span data-stu-id="5e098-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="5e098-111">此函式無法標示為使用者程式碼，因為它不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="5e098-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e098-112">備註</span><span class="sxs-lookup"><span data-stu-id="5e098-112">Remarks</span></span>  
 <span data-ttu-id="5e098-113">Just My Code 步進會略過的非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="5e098-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="5e098-114">使用者程式碼必須是可偵錯的程式碼的子集。</span><span class="sxs-lookup"><span data-stu-id="5e098-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e098-115">需求</span><span class="sxs-lookup"><span data-stu-id="5e098-115">Requirements</span></span>  
 <span data-ttu-id="5e098-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e098-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e098-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e098-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e098-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e098-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e098-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e098-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
