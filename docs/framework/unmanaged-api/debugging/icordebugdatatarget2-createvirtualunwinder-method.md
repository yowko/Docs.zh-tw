---
title: ICorDebugDataTarget2::CreateVirtualUnwinder 方法
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 387dc484b3ada63d62ddc27318e735dfc4ea93b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492266"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="5f5d0-102">ICorDebugDataTarget2::CreateVirtualUnwinder 方法</span><span class="sxs-lookup"><span data-stu-id="5f5d0-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="5f5d0-103">建立新的堆疊 unwinder，以從初始內容 (不一定是執行緒的分葉) 開始回溯。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f5d0-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f5d0-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f5d0-105">Parameters</span></span>  
 <span data-ttu-id="5f5d0-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="5f5d0-106">nativeThreadID</span></span>  
 <span data-ttu-id="5f5d0-107">[in] 其堆疊未回溯之執行緒的原生執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="5f5d0-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="5f5d0-108">contextFlags</span></span>  
 <span data-ttu-id="5f5d0-109">[in] 指定哪些內容部分會在 `initialContext` 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="5f5d0-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="5f5d0-110">cbContext</span></span>  
 <span data-ttu-id="5f5d0-111">[in] `initialContext` 的大小。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="5f5d0-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="5f5d0-112">initialContext</span></span>  
 <span data-ttu-id="5f5d0-113">[in] 內容中的資料。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="5f5d0-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="5f5d0-114">ppUnwinder</span></span>  
 <span data-ttu-id="5f5d0-115">[out] ICorDebugVirtualUnwinder 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f5d0-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="5f5d0-116">Return Value</span></span>  
 <span data-ttu-id="5f5d0-117">如果成功，則為 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-117">`S_OK` if successful.</span></span> <span data-ttu-id="5f5d0-118">其他任何 `HRESULT` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="5f5d0-119">任何失敗`HRESULT`mscordbi 收到的會視為嚴重錯誤，並造成[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法，以傳回`CORDBG_E_DATA_TARGET_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f5d0-120">備註</span><span class="sxs-lookup"><span data-stu-id="5f5d0-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f5d0-121">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5d0-122">需求</span><span class="sxs-lookup"><span data-stu-id="5f5d0-122">Requirements</span></span>  
 <span data-ttu-id="5f5d0-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f5d0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f5d0-124">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f5d0-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f5d0-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f5d0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f5d0-126">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f5d0-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5d0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f5d0-127">See also</span></span>
- [<span data-ttu-id="5f5d0-128">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="5f5d0-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="5f5d0-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5f5d0-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
