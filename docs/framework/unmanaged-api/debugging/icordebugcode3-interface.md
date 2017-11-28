---
title: "ICorDebugCode3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3
helpviewer_keywords: ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee60d052c65df64b1a753166b301ba0012cdc8e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="753fb-102">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="753fb-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="753fb-103">提供方法，以擴充 「 ICorDebugCode"和"ICorDebugCode2 」 提供 managed 傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="753fb-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="753fb-104">方法</span><span class="sxs-lookup"><span data-stu-id="753fb-104">Methods</span></span>  
  
|<span data-ttu-id="753fb-105">方法</span><span class="sxs-lookup"><span data-stu-id="753fb-105">Method</span></span>|<span data-ttu-id="753fb-106">說明</span><span class="sxs-lookup"><span data-stu-id="753fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="753fb-107">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="753fb-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="753fb-108">針對指定的 IL 位移，取得原生位移中斷點放置的位置，讓偵錯工具可以從函式取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="753fb-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="753fb-109">備註</span><span class="sxs-lookup"><span data-stu-id="753fb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="753fb-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="753fb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="753fb-111">需求</span><span class="sxs-lookup"><span data-stu-id="753fb-111">Requirements</span></span>  
 <span data-ttu-id="753fb-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="753fb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="753fb-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="753fb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="753fb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="753fb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="753fb-115">**.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="753fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="753fb-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="753fb-117">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="753fb-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="753fb-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="753fb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
