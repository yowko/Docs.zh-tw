---
title: ICorDebugNativeFrame::CanSetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: d266ec7f82d7d4c7c66f137aafc1c8865d6f8889
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792809"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="72f34-102">ICorDebugNativeFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="72f34-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="72f34-103">取得 HRESULT，指出是否可以安全地將指令指標（IP）設定為機器碼中的指定位移位置。</span><span class="sxs-lookup"><span data-stu-id="72f34-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f34-104">語法</span><span class="sxs-lookup"><span data-stu-id="72f34-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72f34-105">參數</span><span class="sxs-lookup"><span data-stu-id="72f34-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="72f34-106">在指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="72f34-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72f34-107">備註</span><span class="sxs-lookup"><span data-stu-id="72f34-107">Remarks</span></span>  
 <span data-ttu-id="72f34-108">呼叫[ICorDebugNativeFrame：： SetIP](icordebugnativeframe-setip-method.md)方法之前，請先使用 `CanSetIP` 方法。</span><span class="sxs-lookup"><span data-stu-id="72f34-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="72f34-109">如果 `CanSetIP` 會傳回 S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugNativeFrame::SetIP`，但不保證偵錯工具會繼續安全且正確地執行正在進行調試的程式碼。</span><span class="sxs-lookup"><span data-stu-id="72f34-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72f34-110">需求</span><span class="sxs-lookup"><span data-stu-id="72f34-110">Requirements</span></span>  
 <span data-ttu-id="72f34-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72f34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72f34-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72f34-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72f34-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72f34-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72f34-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72f34-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f34-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="72f34-115">See also</span></span>
