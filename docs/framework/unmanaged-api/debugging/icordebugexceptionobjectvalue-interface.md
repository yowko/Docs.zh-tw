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
ms.openlocfilehash: a5762079861f04e1869b206c3200c3a024c1b77a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091001"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="4b806-102">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="4b806-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="4b806-103">擴充 "ICorDebugObjectValue" 介面，以從 managed 例外狀況物件提供堆疊追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="4b806-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b806-104">方法</span><span class="sxs-lookup"><span data-stu-id="4b806-104">Methods</span></span>  
  
|<span data-ttu-id="4b806-105">方法</span><span class="sxs-lookup"><span data-stu-id="4b806-105">Method</span></span>|<span data-ttu-id="4b806-106">描述</span><span class="sxs-lookup"><span data-stu-id="4b806-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b806-107">EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="4b806-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="4b806-108">取得內嵌在例外狀況物件中之呼叫堆疊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4b806-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b806-109">備註</span><span class="sxs-lookup"><span data-stu-id="4b806-109">Remarks</span></span>  
 <span data-ttu-id="4b806-110">針對衍生自 <xref:System.Exception?displayProperty=nameWithType>的 managed 物件，`QueryInterface` 的呼叫將會成功。</span><span class="sxs-lookup"><span data-stu-id="4b806-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b806-111">需求</span><span class="sxs-lookup"><span data-stu-id="4b806-111">Requirements</span></span>  
 <span data-ttu-id="4b806-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b806-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b806-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b806-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b806-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b806-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b806-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b806-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b806-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b806-116">See also</span></span>

- [<span data-ttu-id="4b806-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4b806-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4b806-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="4b806-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
