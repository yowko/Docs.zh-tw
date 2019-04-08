---
title: ICorDebugExceptionObjectValue 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5328442ceaee05b3f81466b785f04a361d456a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098477"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="a368d-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="a368d-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="a368d-103">會擴充 「 ICorDebugObjectValue 」 介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="a368d-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a368d-104">方法</span><span class="sxs-lookup"><span data-stu-id="a368d-104">Methods</span></span>  
  
|<span data-ttu-id="a368d-105">方法</span><span class="sxs-lookup"><span data-stu-id="a368d-105">Method</span></span>|<span data-ttu-id="a368d-106">描述</span><span class="sxs-lookup"><span data-stu-id="a368d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a368d-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="a368d-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="a368d-108">取得列舉值例外狀況物件中內嵌的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="a368d-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a368d-109">備註</span><span class="sxs-lookup"><span data-stu-id="a368d-109">Remarks</span></span>  
 <span data-ttu-id="a368d-110">若要在呼叫`QueryInterface`受管理的物件衍生自會成功<xref:System.Exception?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a368d-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a368d-111">需求</span><span class="sxs-lookup"><span data-stu-id="a368d-111">Requirements</span></span>  
 <span data-ttu-id="a368d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a368d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a368d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a368d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a368d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a368d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a368d-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="a368d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a368d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a368d-116">See also</span></span>

- [<span data-ttu-id="a368d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a368d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a368d-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="a368d-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
