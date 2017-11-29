---
title: "ICorDebugStaticFieldSymbol 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b747d2d43fd7ff4dc901dff14277dbce9606497f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="ebd9d-102">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="ebd9d-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="ebd9d-103">代表靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebd9d-104">方法</span><span class="sxs-lookup"><span data-stu-id="ebd9d-104">Methods</span></span>  
  
|<span data-ttu-id="ebd9d-105">方法</span><span class="sxs-lookup"><span data-stu-id="ebd9d-105">Method</span></span>|<span data-ttu-id="ebd9d-106">說明</span><span class="sxs-lookup"><span data-stu-id="ebd9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebd9d-107">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="ebd9d-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="ebd9d-108">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="ebd9d-109">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="ebd9d-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="ebd9d-110">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="ebd9d-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="ebd9d-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="ebd9d-112">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebd9d-113">備註</span><span class="sxs-lookup"><span data-stu-id="ebd9d-113">Remarks</span></span>  
 <span data-ttu-id="ebd9d-114">`ICorDebugStaticFieldSymbol` 介面可用來擷取靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebd9d-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ebd9d-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd9d-117">需求</span><span class="sxs-lookup"><span data-stu-id="ebd9d-117">Requirements</span></span>  
 <span data-ttu-id="ebd9d-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd9d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd9d-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebd9d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebd9d-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebd9d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebd9d-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd9d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd9d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebd9d-122">See Also</span></span>  
 [<span data-ttu-id="ebd9d-123">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="ebd9d-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="ebd9d-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ebd9d-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ebd9d-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="ebd9d-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
