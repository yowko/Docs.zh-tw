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
ms.openlocfilehash: fa154d0bb48f4ecd4fc6a50ce22fd13c592b7c40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782739"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="aab54-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="aab54-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="aab54-103">擴充 "ICorDebugObjectValue" 介面，以從 managed 例外狀況物件提供堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="aab54-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aab54-104">方法</span><span class="sxs-lookup"><span data-stu-id="aab54-104">Methods</span></span>  
  
|<span data-ttu-id="aab54-105">方法</span><span class="sxs-lookup"><span data-stu-id="aab54-105">Method</span></span>|<span data-ttu-id="aab54-106">描述</span><span class="sxs-lookup"><span data-stu-id="aab54-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aab54-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="aab54-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="aab54-108">取得內嵌在例外狀況物件中之呼叫堆疊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="aab54-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aab54-109">備註</span><span class="sxs-lookup"><span data-stu-id="aab54-109">Remarks</span></span>  
 <span data-ttu-id="aab54-110">針對衍生自 <xref:System.Exception?displayProperty=nameWithType>的 managed 物件，`QueryInterface` 的呼叫將會成功。</span><span class="sxs-lookup"><span data-stu-id="aab54-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aab54-111">需求</span><span class="sxs-lookup"><span data-stu-id="aab54-111">Requirements</span></span>  
 <span data-ttu-id="aab54-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aab54-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aab54-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aab54-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aab54-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aab54-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aab54-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aab54-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab54-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="aab54-116">See also</span></span>

- [<span data-ttu-id="aab54-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="aab54-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="aab54-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="aab54-118">Debugging</span></span>](index.md)
