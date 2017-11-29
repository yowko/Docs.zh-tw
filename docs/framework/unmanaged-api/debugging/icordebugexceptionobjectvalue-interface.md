---
title: "ICorDebugExceptionObjectValue 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 47733a6af18d42d0d9db1e50cf21646289ef1443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="fdabd-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="fdabd-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="fdabd-103">擴充的 」 ICorDebugObjectValue 」 介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="fdabd-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdabd-104">方法</span><span class="sxs-lookup"><span data-stu-id="fdabd-104">Methods</span></span>  
  
|<span data-ttu-id="fdabd-105">方法</span><span class="sxs-lookup"><span data-stu-id="fdabd-105">Method</span></span>|<span data-ttu-id="fdabd-106">說明</span><span class="sxs-lookup"><span data-stu-id="fdabd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdabd-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="fdabd-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="fdabd-108">取得列舉值例外狀況物件中內嵌的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="fdabd-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdabd-109">備註</span><span class="sxs-lookup"><span data-stu-id="fdabd-109">Remarks</span></span>  
 <span data-ttu-id="fdabd-110">若要呼叫`QueryInterface`衍生自的受管理物件將會成功<xref:System.Exception?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fdabd-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdabd-111">需求</span><span class="sxs-lookup"><span data-stu-id="fdabd-111">Requirements</span></span>  
 <span data-ttu-id="fdabd-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fdabd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdabd-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdabd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdabd-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdabd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdabd-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdabd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdabd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdabd-116">See Also</span></span>  
 [<span data-ttu-id="fdabd-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fdabd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fdabd-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="fdabd-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
