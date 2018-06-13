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
ms.openlocfilehash: d6805b7b49f76b80161aef5051fe3c284192f582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413770"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="8e140-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="8e140-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="8e140-103">擴充的 」 ICorDebugObjectValue 」 介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="8e140-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e140-104">方法</span><span class="sxs-lookup"><span data-stu-id="8e140-104">Methods</span></span>  
  
|<span data-ttu-id="8e140-105">方法</span><span class="sxs-lookup"><span data-stu-id="8e140-105">Method</span></span>|<span data-ttu-id="8e140-106">描述</span><span class="sxs-lookup"><span data-stu-id="8e140-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e140-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="8e140-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="8e140-108">取得列舉值例外狀況物件中內嵌的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="8e140-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e140-109">備註</span><span class="sxs-lookup"><span data-stu-id="8e140-109">Remarks</span></span>  
 <span data-ttu-id="8e140-110">若要呼叫`QueryInterface`衍生自的受管理物件將會成功<xref:System.Exception?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8e140-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e140-111">需求</span><span class="sxs-lookup"><span data-stu-id="8e140-111">Requirements</span></span>  
 <span data-ttu-id="8e140-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e140-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e140-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e140-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e140-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e140-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e140-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e140-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e140-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e140-116">See Also</span></span>  
 [<span data-ttu-id="8e140-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8e140-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8e140-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="8e140-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
