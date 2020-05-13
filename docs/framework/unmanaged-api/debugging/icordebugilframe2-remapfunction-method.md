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
ms.openlocfilehash: 43f585417ed52b92c23087c0f02fd188ee09ea7e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210211"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="722b9-102">ICorDebugILFrame2::RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="722b9-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="722b9-103">藉由指定新的 Microsoft 中繼語言（MSIL）位移來重新對應已編輯的函式</span><span class="sxs-lookup"><span data-stu-id="722b9-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="722b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="722b9-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="722b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="722b9-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="722b9-106">在應該放置指令指標的堆疊框架新 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="722b9-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="722b9-107">這個值必須是序列點。</span><span class="sxs-lookup"><span data-stu-id="722b9-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="722b9-108">呼叫者必須負責確保此值的有效性。</span><span class="sxs-lookup"><span data-stu-id="722b9-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="722b9-109">例如，如果 MSIL 位移超出函式的界限，則為無效。</span><span class="sxs-lookup"><span data-stu-id="722b9-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="722b9-110">備註</span><span class="sxs-lookup"><span data-stu-id="722b9-110">Remarks</span></span>  
 <span data-ttu-id="722b9-111">編輯方塊架的函式之後，偵錯工具可以呼叫 `RemapFunction` 方法，以在框架函式的最新版本中交換，以便執行此功能。</span><span class="sxs-lookup"><span data-stu-id="722b9-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="722b9-112">程式碼執行將從給定的 MSIL 位移開始。</span><span class="sxs-lookup"><span data-stu-id="722b9-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="722b9-113">呼叫 `RemapFunction` （例如呼叫[ICorDebugILFrame：： SetIP](icordebugilframe-setip-method.md)）會立即使與產生執行緒堆疊追蹤相關的所有偵錯工具失效。</span><span class="sxs-lookup"><span data-stu-id="722b9-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="722b9-114">這些介面包括[ICorDebugChain](icordebugchain-interface.md)、ICorDebugILFrame、ICorDebugInternalFrame 和 ICorDebugNativeFrame。</span><span class="sxs-lookup"><span data-stu-id="722b9-114">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="722b9-115">`RemapFunction`方法只能在目前框架的內容中呼叫，而且只有在下列其中一個案例中：</span><span class="sxs-lookup"><span data-stu-id="722b9-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="722b9-116">在收到尚未繼續的[ICorDebugManagedCallback2：： FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md)回呼之後。</span><span class="sxs-lookup"><span data-stu-id="722b9-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="722b9-117">由於此框架的[ICorDebugManagedCallback：： EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md)事件，程式碼執行已停止。</span><span class="sxs-lookup"><span data-stu-id="722b9-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="722b9-118">需求</span><span class="sxs-lookup"><span data-stu-id="722b9-118">Requirements</span></span>  
 <span data-ttu-id="722b9-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="722b9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="722b9-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="722b9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="722b9-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="722b9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="722b9-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="722b9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
