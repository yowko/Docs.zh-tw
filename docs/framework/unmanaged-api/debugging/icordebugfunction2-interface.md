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
ms.openlocfilehash: d9e84a70d72db1338c80140ce3350774bfae4bca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726271"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="b2855-102">ICorDebugFunction2 介面</span><span class="sxs-lookup"><span data-stu-id="b2855-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="b2855-103">以邏輯方式擴充 ICorDebugFunction 介面，以提供 Just My Code 逐步執行偵錯工具的支援，這會略過非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2855-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2855-104">方法</span><span class="sxs-lookup"><span data-stu-id="b2855-104">Methods</span></span>  
  
|<span data-ttu-id="b2855-105">方法</span><span class="sxs-lookup"><span data-stu-id="b2855-105">Method</span></span>|<span data-ttu-id="b2855-106">描述</span><span class="sxs-lookup"><span data-stu-id="b2855-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2855-107">EnumerateNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="b2855-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="b2855-108">尚未執行 (。 ) 取得 ICorDebugCodeEnum 的介面指標，其中包含這個 ICorDebugFunction2 物件所參考之函式中的機器碼語句。</span><span class="sxs-lookup"><span data-stu-id="b2855-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="b2855-109">GetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="b2855-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="b2855-110">取得值，這個值會指出此函式是否標記為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2855-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="b2855-111">GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="b2855-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="b2855-112">取得此函式的編輯後繼續版本。</span><span class="sxs-lookup"><span data-stu-id="b2855-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="b2855-113">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="b2855-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="b2855-114">將此函數標記為 Just My Code 逐步執行。</span><span class="sxs-lookup"><span data-stu-id="b2855-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2855-115">備註</span><span class="sxs-lookup"><span data-stu-id="b2855-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2855-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b2855-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2855-117">需求</span><span class="sxs-lookup"><span data-stu-id="b2855-117">Requirements</span></span>  

 <span data-ttu-id="b2855-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2855-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2855-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2855-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2855-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2855-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2855-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2855-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2855-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2855-122">See also</span></span>

- [<span data-ttu-id="b2855-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b2855-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
