---
title: "ICorDebugUnmanagedCallback 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback
helpviewer_keywords: ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa104bee5171b3b28731cf18a4d26e32f49169ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="3d719-102">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3d719-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="3d719-103">提供原生 common language runtime (CLR) 沒有直接相關的事件的通知。</span><span class="sxs-lookup"><span data-stu-id="3d719-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d719-104">方法</span><span class="sxs-lookup"><span data-stu-id="3d719-104">Methods</span></span>  
  
|<span data-ttu-id="3d719-105">方法</span><span class="sxs-lookup"><span data-stu-id="3d719-105">Method</span></span>|<span data-ttu-id="3d719-106">說明</span><span class="sxs-lookup"><span data-stu-id="3d719-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d719-107">DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="3d719-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="3d719-108">原生事件已引發會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="3d719-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d719-109">備註</span><span class="sxs-lookup"><span data-stu-id="3d719-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d719-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="3d719-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d719-111">需求</span><span class="sxs-lookup"><span data-stu-id="3d719-111">Requirements</span></span>  
 <span data-ttu-id="3d719-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d719-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d719-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d719-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d719-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d719-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d719-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d719-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d719-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d719-116">See Also</span></span>  
 [<span data-ttu-id="3d719-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3d719-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
