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
ms.openlocfilehash: 8e4f745440936a39e22faf60d10a05a0bb110606
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975949"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="46025-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="46025-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="46025-103">擴充 "ICorDebugObjectValue" 介面，以從 managed 例外狀況物件提供堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="46025-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46025-104">方法</span><span class="sxs-lookup"><span data-stu-id="46025-104">Methods</span></span>  
  
|<span data-ttu-id="46025-105">方法</span><span class="sxs-lookup"><span data-stu-id="46025-105">Method</span></span>|<span data-ttu-id="46025-106">描述</span><span class="sxs-lookup"><span data-stu-id="46025-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46025-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="46025-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="46025-108">取得內嵌在例外狀況物件中之呼叫堆疊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="46025-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46025-109">備註</span><span class="sxs-lookup"><span data-stu-id="46025-109">Remarks</span></span>  
 <span data-ttu-id="46025-110">針對衍生自`QueryInterface` <xref:System.Exception?displayProperty=nameWithType>的 managed 物件，對的呼叫將會成功。</span><span class="sxs-lookup"><span data-stu-id="46025-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46025-111">需求</span><span class="sxs-lookup"><span data-stu-id="46025-111">Requirements</span></span>  
 <span data-ttu-id="46025-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46025-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46025-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46025-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46025-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46025-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46025-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46025-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46025-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46025-116">See also</span></span>

- [<span data-ttu-id="46025-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="46025-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="46025-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="46025-118">Debugging</span></span>](index.md)
