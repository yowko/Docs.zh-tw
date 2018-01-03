---
title: "ICorDebugILFrame2::RemapFunction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9fed4759576d1b6d2fec1a5e9c1e36019e5944c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="7f706-102">ICorDebugILFrame2::RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="7f706-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="7f706-103">藉由指定新的 Microsoft intermediate language (MSIL) 位移重新對應已編輯函式</span><span class="sxs-lookup"><span data-stu-id="7f706-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f706-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f706-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f706-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f706-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="7f706-106">[in]堆疊框架的新 MSIL 指令指標應該將放入其中的位移。</span><span class="sxs-lookup"><span data-stu-id="7f706-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="7f706-107">此值必須是序列點。</span><span class="sxs-lookup"><span data-stu-id="7f706-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="7f706-108">它是呼叫者的責任在於確保此值的有效性。</span><span class="sxs-lookup"><span data-stu-id="7f706-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="7f706-109">比方說，MSIL 位移不正確，如果它是函式的範圍外。</span><span class="sxs-lookup"><span data-stu-id="7f706-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f706-110">備註</span><span class="sxs-lookup"><span data-stu-id="7f706-110">Remarks</span></span>  
 <span data-ttu-id="7f706-111">當已經編輯框架的函式時，偵錯工具可以呼叫`RemapFunction`交換中框架的函式的最新版本，讓它可以執行的方法。</span><span class="sxs-lookup"><span data-stu-id="7f706-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="7f706-112">執行程式碼將會開始於指定的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="7f706-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f706-113">呼叫`RemapFunction`、 like 呼叫[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)，將會立即使產生執行緒的堆疊追蹤相關的所有偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="7f706-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="7f706-114">這些介面包括[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)，ICorDebugILFrame、 ICorDebugInternalFrame 和 ICorDebugNativeFrame。</span><span class="sxs-lookup"><span data-stu-id="7f706-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="7f706-115">`RemapFunction`可呼叫方法，只在目前的框架，內容中，且只有在下列情況的其中一個：</span><span class="sxs-lookup"><span data-stu-id="7f706-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
-   <span data-ttu-id="7f706-116">在回條之後[icordebugmanagedcallback2:: Functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)具有未尚未已繼續的回呼。</span><span class="sxs-lookup"><span data-stu-id="7f706-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
-   <span data-ttu-id="7f706-117">因為停止執行程式碼時[icordebugmanagedcallback:: Editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)這個畫面格的事件。</span><span class="sxs-lookup"><span data-stu-id="7f706-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f706-118">需求</span><span class="sxs-lookup"><span data-stu-id="7f706-118">Requirements</span></span>  
 <span data-ttu-id="7f706-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f706-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f706-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f706-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f706-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f706-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f706-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f706-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
