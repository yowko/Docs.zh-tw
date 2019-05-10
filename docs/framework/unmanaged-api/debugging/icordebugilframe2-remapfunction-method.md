---
title: ICorDebugILFrame2::RemapFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbec4a4ba05a7e6d50f9740582415219eafb1e57
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621475"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="10b3c-102">ICorDebugILFrame2::RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="10b3c-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="10b3c-103">將編輯過的函式藉由指定新的 Microsoft intermediate language (MSIL) 位移重新對應</span><span class="sxs-lookup"><span data-stu-id="10b3c-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b3c-104">語法</span><span class="sxs-lookup"><span data-stu-id="10b3c-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10b3c-105">參數</span><span class="sxs-lookup"><span data-stu-id="10b3c-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="10b3c-106">[in]堆疊框架的新 MSIL 位移應該放置指令指標。</span><span class="sxs-lookup"><span data-stu-id="10b3c-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="10b3c-107">此值必須是序列點。</span><span class="sxs-lookup"><span data-stu-id="10b3c-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="10b3c-108">是以確保此值之有效性的呼叫者的責任。</span><span class="sxs-lookup"><span data-stu-id="10b3c-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="10b3c-109">比方說，MSIL 位移不超出界限的函式是否有效。</span><span class="sxs-lookup"><span data-stu-id="10b3c-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10b3c-110">備註</span><span class="sxs-lookup"><span data-stu-id="10b3c-110">Remarks</span></span>  
 <span data-ttu-id="10b3c-111">偵錯工具時已編輯框架的函式，可以呼叫`RemapFunction`交換中框架的函式的最新版本，因此可以執行的方法。</span><span class="sxs-lookup"><span data-stu-id="10b3c-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="10b3c-112">執行程式碼將會在指定的 MSIL 位移開始。</span><span class="sxs-lookup"><span data-stu-id="10b3c-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10b3c-113">呼叫`RemapFunction`，例如呼叫[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)，將會立即失效與產生的執行緒堆疊追蹤相關的所有偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="10b3c-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="10b3c-114">這些介面包括[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)，ICorDebugILFrame、 ICorDebugInternalFrame 和 ICorDebugNativeFrame。</span><span class="sxs-lookup"><span data-stu-id="10b3c-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="10b3c-115">`RemapFunction`可以呼叫方法，只在目前的框架的內容中，而且只用於下列案例之一：</span><span class="sxs-lookup"><span data-stu-id="10b3c-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="10b3c-116">之後的回條[ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)已不還繼續執行的回呼。</span><span class="sxs-lookup"><span data-stu-id="10b3c-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="10b3c-117">因為停止執行程式碼時[icordebugmanagedcallback:: Editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)這個框架的事件。</span><span class="sxs-lookup"><span data-stu-id="10b3c-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10b3c-118">需求</span><span class="sxs-lookup"><span data-stu-id="10b3c-118">Requirements</span></span>  
 <span data-ttu-id="10b3c-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10b3c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10b3c-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10b3c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10b3c-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10b3c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10b3c-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10b3c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
