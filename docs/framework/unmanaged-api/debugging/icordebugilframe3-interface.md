---
title: "ICorDebugILFrame3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame3
api_location: mscordbi.dll
api_type: COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe6affcf82a16a4fd51a5e5a4bf33b247dae0688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="cdb4b-102">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="cdb4b-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="cdb4b-103">提供封裝函式傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="cdb4b-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="cdb4b-104">`ICorDebugILFrame3`是的 ICorDebugILFrame 和 ICorDebugILFrame2 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="cdb4b-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cdb4b-105">方法</span><span class="sxs-lookup"><span data-stu-id="cdb4b-105">Methods</span></span>  
  
|<span data-ttu-id="cdb4b-106">方法</span><span class="sxs-lookup"><span data-stu-id="cdb4b-106">Method</span></span>|<span data-ttu-id="cdb4b-107">說明</span><span class="sxs-lookup"><span data-stu-id="cdb4b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cdb4b-108">GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="cdb4b-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="cdb4b-109">取得封裝函式的傳回值的 ICorDebugValue 物件。</span><span class="sxs-lookup"><span data-stu-id="cdb4b-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdb4b-110">備註</span><span class="sxs-lookup"><span data-stu-id="cdb4b-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdb4b-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="cdb4b-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdb4b-112">需求</span><span class="sxs-lookup"><span data-stu-id="cdb4b-112">Requirements</span></span>  
 <span data-ttu-id="cdb4b-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb4b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdb4b-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdb4b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdb4b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdb4b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdb4b-116">**.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb4b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb4b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdb4b-117">See Also</span></span>  
 [<span data-ttu-id="cdb4b-118">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="cdb4b-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="cdb4b-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cdb4b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
