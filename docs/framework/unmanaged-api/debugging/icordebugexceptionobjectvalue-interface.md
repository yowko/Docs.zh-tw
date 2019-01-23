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
ms.openlocfilehash: c1baae7d7867b0cbb227af72fcc505a5cadfa4df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511625"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="7b183-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="7b183-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="7b183-103">會擴充 「 ICorDebugObjectValue 」 介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="7b183-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b183-104">方法</span><span class="sxs-lookup"><span data-stu-id="7b183-104">Methods</span></span>  
  
|<span data-ttu-id="7b183-105">方法</span><span class="sxs-lookup"><span data-stu-id="7b183-105">Method</span></span>|<span data-ttu-id="7b183-106">描述</span><span class="sxs-lookup"><span data-stu-id="7b183-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b183-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="7b183-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="7b183-108">取得列舉值例外狀況物件中內嵌的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="7b183-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b183-109">備註</span><span class="sxs-lookup"><span data-stu-id="7b183-109">Remarks</span></span>  
 <span data-ttu-id="7b183-110">若要在呼叫`QueryInterface`受管理的物件衍生自會成功<xref:System.Exception?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7b183-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b183-111">需求</span><span class="sxs-lookup"><span data-stu-id="7b183-111">Requirements</span></span>  
 <span data-ttu-id="7b183-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b183-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b183-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b183-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b183-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b183-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b183-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b183-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b183-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b183-116">See also</span></span>
- [<span data-ttu-id="7b183-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7b183-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7b183-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="7b183-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

