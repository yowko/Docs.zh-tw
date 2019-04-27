---
title: ICorDebugMDA 介面
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916665"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="da742-102">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="da742-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="da742-103">表示 Managed 偵錯助理 (MDA) 訊息。</span><span class="sxs-lookup"><span data-stu-id="da742-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da742-104">方法</span><span class="sxs-lookup"><span data-stu-id="da742-104">Methods</span></span>  
  
|<span data-ttu-id="da742-105">方法</span><span class="sxs-lookup"><span data-stu-id="da742-105">Method</span></span>|<span data-ttu-id="da742-106">描述</span><span class="sxs-lookup"><span data-stu-id="da742-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da742-107">GetDescription 方法</span><span class="sxs-lookup"><span data-stu-id="da742-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="da742-108">取得字串，包含此 MDA 的描述。</span><span class="sxs-lookup"><span data-stu-id="da742-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="da742-109">GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="da742-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="da742-110">取得與這個 MDA 相關聯的旗標。</span><span class="sxs-lookup"><span data-stu-id="da742-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="da742-111">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="da742-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="da742-112">取得字串，包含此 MDA 的名稱。</span><span class="sxs-lookup"><span data-stu-id="da742-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="da742-113">GetOSThreadId 方法</span><span class="sxs-lookup"><span data-stu-id="da742-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="da742-114">取得此 MDA 賴以執行的作業系統執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="da742-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="da742-115">GetXML 方法</span><span class="sxs-lookup"><span data-stu-id="da742-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="da742-116">取得與這個 MDA 相關聯的完整 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="da742-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da742-117">備註</span><span class="sxs-lookup"><span data-stu-id="da742-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da742-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="da742-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da742-119">需求</span><span class="sxs-lookup"><span data-stu-id="da742-119">Requirements</span></span>  
 <span data-ttu-id="da742-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da742-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da742-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da742-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da742-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da742-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da742-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da742-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da742-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da742-124">See also</span></span>

- [<span data-ttu-id="da742-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="da742-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="da742-126">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="da742-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
