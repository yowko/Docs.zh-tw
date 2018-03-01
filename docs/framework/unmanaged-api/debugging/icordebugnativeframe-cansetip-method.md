---
title: "ICorDebugNativeFrame::CanSetIP 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b87ff9ae71b916a9a1141c2e5fedce7f79fbcd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="e70f1-102">ICorDebugNativeFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="e70f1-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="e70f1-103">取得 HRESULT，表示是否以原生程式碼中，設定為指定的位移位置的指令指標 (IP) 安全。</span><span class="sxs-lookup"><span data-stu-id="e70f1-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e70f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="e70f1-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e70f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="e70f1-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="e70f1-106">[in]指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="e70f1-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e70f1-107">備註</span><span class="sxs-lookup"><span data-stu-id="e70f1-107">Remarks</span></span>  
 <span data-ttu-id="e70f1-108">使用`CanSetIP`方法之前呼叫[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e70f1-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="e70f1-109">如果`CanSetIP`任何的 HRESULT 傳回以外 S_OK 時，您可以仍然叫用`ICorDebugNativeFrame::SetIP`，但不保證偵錯工具會繼續進行偵錯的程式碼的安全且正確執行。</span><span class="sxs-lookup"><span data-stu-id="e70f1-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e70f1-110">需求</span><span class="sxs-lookup"><span data-stu-id="e70f1-110">Requirements</span></span>  
 <span data-ttu-id="e70f1-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e70f1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e70f1-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e70f1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e70f1-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e70f1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e70f1-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e70f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70f1-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e70f1-115">See Also</span></span>  
 
