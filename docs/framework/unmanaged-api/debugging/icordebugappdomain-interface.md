---
title: ICorDebugAppDomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aab18cb1d29931a58e64561f23d91ee4eb3a4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="8dd39-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="8dd39-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="8dd39-103">提供偵錯應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="8dd39-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="8dd39-104">這個介面是 ICorDebugController 的子類別。</span><span class="sxs-lookup"><span data-stu-id="8dd39-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8dd39-105">方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-105">Methods</span></span>  
  
|<span data-ttu-id="8dd39-106">方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-106">Method</span></span>|<span data-ttu-id="8dd39-107">描述</span><span class="sxs-lookup"><span data-stu-id="8dd39-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8dd39-108">Attach 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="8dd39-109">將偵錯工具附加至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="8dd39-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="8dd39-110">EnumerateAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="8dd39-111">取得應用程式定義域中之組件列舉值。</span><span class="sxs-lookup"><span data-stu-id="8dd39-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="8dd39-112">EnumerateBreakpoints 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="8dd39-113">應用程式定義域中取得所有作用中的中斷點的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8dd39-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="8dd39-114">EnumerateSteppers 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="8dd39-115">應用程式定義域中取得所有作用中的 stepper 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8dd39-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="8dd39-116">GetId 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="8dd39-117">取得應用程式定義域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="8dd39-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="8dd39-118">GetModuleFromMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="8dd39-119">取得與指定的中繼資料介面的 ICorDebugModule 物件。</span><span class="sxs-lookup"><span data-stu-id="8dd39-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="8dd39-120">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="8dd39-121">取得應用程式定義域的名稱。</span><span class="sxs-lookup"><span data-stu-id="8dd39-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="8dd39-122">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="8dd39-123">Common language runtime (CLR) 應用程式定義域中取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="8dd39-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="8dd39-124">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="8dd39-125">取得包含在應用程式定義域的處理序。</span><span class="sxs-lookup"><span data-stu-id="8dd39-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="8dd39-126">IsAttached 方法</span><span class="sxs-lookup"><span data-stu-id="8dd39-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="8dd39-127">決定是否要將偵錯工具附加至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="8dd39-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dd39-128">備註</span><span class="sxs-lookup"><span data-stu-id="8dd39-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dd39-129">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8dd39-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dd39-130">需求</span><span class="sxs-lookup"><span data-stu-id="8dd39-130">Requirements</span></span>  
 <span data-ttu-id="8dd39-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd39-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dd39-132">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8dd39-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8dd39-133">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8dd39-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8dd39-134">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dd39-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd39-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd39-135">See Also</span></span>  
 [<span data-ttu-id="8dd39-136">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8dd39-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
