---
title: ICorDebugFunction2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: 611091d39da6d7f646457457f20ce1eaf37db361
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213201"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="9931a-102">ICorDebugFunction2 介面</span><span class="sxs-lookup"><span data-stu-id="9931a-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="9931a-103">以邏輯方式擴充 ICorDebugFunction 介面，以支援 Just My Code 的逐步執行偵測，這會略過非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="9931a-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9931a-104">方法</span><span class="sxs-lookup"><span data-stu-id="9931a-104">Methods</span></span>  
  
|<span data-ttu-id="9931a-105">方法</span><span class="sxs-lookup"><span data-stu-id="9931a-105">Method</span></span>|<span data-ttu-id="9931a-106">描述</span><span class="sxs-lookup"><span data-stu-id="9931a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9931a-107">EnumerateNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="9931a-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="9931a-108">（尚未執行）。取得 ICorDebugCodeEnum 的介面指標，其中包含這個 ICorDebugFunction2 物件所參考之函式中的機器碼語句。</span><span class="sxs-lookup"><span data-stu-id="9931a-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="9931a-109">GetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="9931a-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="9931a-110">取得值，指出此函式是否標示為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="9931a-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="9931a-111">GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="9931a-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="9931a-112">取得此函式的編輯後繼續版本。</span><span class="sxs-lookup"><span data-stu-id="9931a-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="9931a-113">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="9931a-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="9931a-114">將此函數標示為 Just My Code 逐步執行。</span><span class="sxs-lookup"><span data-stu-id="9931a-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9931a-115">備註</span><span class="sxs-lookup"><span data-stu-id="9931a-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9931a-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="9931a-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9931a-117">需求</span><span class="sxs-lookup"><span data-stu-id="9931a-117">Requirements</span></span>  
 <span data-ttu-id="9931a-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9931a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9931a-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9931a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9931a-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9931a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9931a-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9931a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9931a-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="9931a-122">See also</span></span>

- [<span data-ttu-id="9931a-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9931a-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
