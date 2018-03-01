---
title: "ICorDebugExceptionObjectValue 介面"
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
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6ee743a5e3e28b5d8b864f325239725ca6c0042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="c7497-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="c7497-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="c7497-103">擴充的 」 ICorDebugObjectValue 」 介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="c7497-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7497-104">方法</span><span class="sxs-lookup"><span data-stu-id="c7497-104">Methods</span></span>  
  
|<span data-ttu-id="c7497-105">方法</span><span class="sxs-lookup"><span data-stu-id="c7497-105">Method</span></span>|<span data-ttu-id="c7497-106">描述</span><span class="sxs-lookup"><span data-stu-id="c7497-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7497-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="c7497-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="c7497-108">取得列舉值例外狀況物件中內嵌的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="c7497-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7497-109">備註</span><span class="sxs-lookup"><span data-stu-id="c7497-109">Remarks</span></span>  
 <span data-ttu-id="c7497-110">若要呼叫`QueryInterface`衍生自的受管理物件將會成功<xref:System.Exception?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c7497-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7497-111">需求</span><span class="sxs-lookup"><span data-stu-id="c7497-111">Requirements</span></span>  
 <span data-ttu-id="c7497-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7497-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7497-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7497-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7497-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7497-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7497-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7497-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7497-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7497-116">See Also</span></span>  
 [<span data-ttu-id="c7497-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c7497-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c7497-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="c7497-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
