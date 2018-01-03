---
title: ICorDebugInternalFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame
helpviewer_keywords: ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e950847764e695f705aeded0e3804db4b872827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="cf404-102">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="cf404-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="cf404-103">代表執行階段內部堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="cf404-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="cf404-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="cf404-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf404-105">方法</span><span class="sxs-lookup"><span data-stu-id="cf404-105">Methods</span></span>  
  
|<span data-ttu-id="cf404-106">方法</span><span class="sxs-lookup"><span data-stu-id="cf404-106">Method</span></span>|<span data-ttu-id="cf404-107">描述</span><span class="sxs-lookup"><span data-stu-id="cf404-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf404-108">GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="cf404-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="cf404-109">取得這個內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="cf404-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf404-110">備註</span><span class="sxs-lookup"><span data-stu-id="cf404-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf404-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="cf404-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf404-112">需求</span><span class="sxs-lookup"><span data-stu-id="cf404-112">Requirements</span></span>  
 <span data-ttu-id="cf404-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf404-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf404-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf404-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf404-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf404-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf404-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf404-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf404-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf404-117">See Also</span></span>  
 [<span data-ttu-id="cf404-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cf404-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
