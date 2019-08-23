---
title: ICorDebugDataTarget2::CreateVirtualUnwinder 方法
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5445fb223e34aa82d4b93032bb059093978f6bd1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910337"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="7889d-102">ICorDebugDataTarget2::CreateVirtualUnwinder 方法</span><span class="sxs-lookup"><span data-stu-id="7889d-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="7889d-103">建立新的堆疊 unwinder，以從初始內容 (不一定是執行緒的分葉) 開始回溯。</span><span class="sxs-lookup"><span data-stu-id="7889d-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7889d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7889d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="7889d-105">參數</span><span class="sxs-lookup"><span data-stu-id="7889d-105">Parameters</span></span>  
 <span data-ttu-id="7889d-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="7889d-106">nativeThreadID</span></span>  
 <span data-ttu-id="7889d-107">[in] 其堆疊未回溯之執行緒的原生執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="7889d-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="7889d-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="7889d-108">contextFlags</span></span>  
 <span data-ttu-id="7889d-109">[in] 指定哪些內容部分會在 `initialContext` 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="7889d-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="7889d-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="7889d-110">cbContext</span></span>  
 <span data-ttu-id="7889d-111">[in] `initialContext` 的大小。</span><span class="sxs-lookup"><span data-stu-id="7889d-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="7889d-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="7889d-112">initialContext</span></span>  
 <span data-ttu-id="7889d-113">[in] 內容中的資料。</span><span class="sxs-lookup"><span data-stu-id="7889d-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="7889d-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="7889d-114">ppUnwinder</span></span>  
 <span data-ttu-id="7889d-115">[out] ICorDebugVirtualUnwinder 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="7889d-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7889d-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="7889d-116">Return Value</span></span>  
 <span data-ttu-id="7889d-117">如果成功，則為 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="7889d-117">`S_OK` if successful.</span></span> <span data-ttu-id="7889d-118">其他任何 `HRESULT` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="7889d-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="7889d-119">Mscordbi.dll 收到`HRESULT`的任何失敗都會被視為嚴重錯誤, 並導致[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法`CORDBG_E_DATA_TARGET_ERROR`傳回。</span><span class="sxs-lookup"><span data-stu-id="7889d-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7889d-120">備註</span><span class="sxs-lookup"><span data-stu-id="7889d-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7889d-121">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="7889d-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7889d-122">需求</span><span class="sxs-lookup"><span data-stu-id="7889d-122">Requirements</span></span>  
 <span data-ttu-id="7889d-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7889d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7889d-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7889d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7889d-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7889d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7889d-126">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7889d-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7889d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7889d-127">See also</span></span>

- [<span data-ttu-id="7889d-128">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="7889d-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="7889d-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7889d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
