---
title: "ICorDebugNativeFrame::GetIP 方法"
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
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f9ea20577b3132a2378013e7c5fa8356c14c8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="3cf4d-102">ICorDebugNativeFrame::GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="3cf4d-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="3cf4d-103">取得原生程式碼的位移指令指標目前設定的位置。</span><span class="sxs-lookup"><span data-stu-id="3cf4d-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cf4d-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cf4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3cf4d-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="3cf4d-106">[out]原生程式碼的位移位置指標。</span><span class="sxs-lookup"><span data-stu-id="3cf4d-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cf4d-107">備註</span><span class="sxs-lookup"><span data-stu-id="3cf4d-107">Remarks</span></span>  
 <span data-ttu-id="3cf4d-108">這個 「 ICorDebugNativeFrame"所表示之堆疊框架是否在作用中，此位移為下一個要執行指令的位址。</span><span class="sxs-lookup"><span data-stu-id="3cf4d-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="3cf4d-109">如果此堆疊框架不是作用中，此位移為下一個堆疊框架就會重新啟動時要執行指令的位址。</span><span class="sxs-lookup"><span data-stu-id="3cf4d-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cf4d-110">需求</span><span class="sxs-lookup"><span data-stu-id="3cf4d-110">Requirements</span></span>  
 <span data-ttu-id="3cf4d-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf4d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cf4d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3cf4d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cf4d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cf4d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cf4d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cf4d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf4d-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cf4d-115">See Also</span></span>  
 
