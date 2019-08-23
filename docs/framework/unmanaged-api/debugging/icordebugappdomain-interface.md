---
title: ICorDebugAppDomain 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12753ab65f9339e8f6c3049bb72755e87464eb1a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963101"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="58ee3-102">ICorDebugAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="58ee3-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="58ee3-103">提供偵錯應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="58ee3-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="58ee3-104">這個介面是 ICorDebugController 的子類別。</span><span class="sxs-lookup"><span data-stu-id="58ee3-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58ee3-105">方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-105">Methods</span></span>  
  
|<span data-ttu-id="58ee3-106">方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-106">Method</span></span>|<span data-ttu-id="58ee3-107">說明</span><span class="sxs-lookup"><span data-stu-id="58ee3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58ee3-108">Attach 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="58ee3-109">將偵錯工具附加至應用程式域。</span><span class="sxs-lookup"><span data-stu-id="58ee3-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="58ee3-110">EnumerateAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="58ee3-111">取得應用程式域中元件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="58ee3-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="58ee3-112">EnumerateBreakpoints 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="58ee3-113">取得應用程式域中所有使用中中斷點的列舉值。</span><span class="sxs-lookup"><span data-stu-id="58ee3-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="58ee3-114">EnumerateSteppers 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="58ee3-115">取得應用程式域中所有現用 steppers 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="58ee3-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="58ee3-116">GetId 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="58ee3-117">取得應用程式域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="58ee3-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="58ee3-118">GetModuleFromMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="58ee3-119">取得具有指定之中繼資料介面的 ICorDebugModule 物件。</span><span class="sxs-lookup"><span data-stu-id="58ee3-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="58ee3-120">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="58ee3-121">取得應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="58ee3-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="58ee3-122">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="58ee3-123">取得 common language runtime (CLR) 應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="58ee3-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="58ee3-124">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="58ee3-125">取得包含應用程式域的進程。</span><span class="sxs-lookup"><span data-stu-id="58ee3-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="58ee3-126">IsAttached 方法</span><span class="sxs-lookup"><span data-stu-id="58ee3-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="58ee3-127">判斷偵錯工具是否附加至應用程式域。</span><span class="sxs-lookup"><span data-stu-id="58ee3-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58ee3-128">備註</span><span class="sxs-lookup"><span data-stu-id="58ee3-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58ee3-129">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="58ee3-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ee3-130">需求</span><span class="sxs-lookup"><span data-stu-id="58ee3-130">Requirements</span></span>  
 <span data-ttu-id="58ee3-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58ee3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ee3-132">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58ee3-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58ee3-133">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58ee3-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ee3-134">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ee3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ee3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58ee3-135">See also</span></span>

- [<span data-ttu-id="58ee3-136">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58ee3-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
