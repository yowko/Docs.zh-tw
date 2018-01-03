---
title: "ICorDebugDataTarget3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c65bbfa033a3a585cdcfdb42cdda95f1de4aa412
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="de6c9-102">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="de6c9-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="de6c9-103">以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="de6c9-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="de6c9-104">方法</span><span class="sxs-lookup"><span data-stu-id="de6c9-104">Method</span></span>  
  
|<span data-ttu-id="de6c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="de6c9-105">Method</span></span>|<span data-ttu-id="de6c9-106">描述</span><span class="sxs-lookup"><span data-stu-id="de6c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de6c9-107">GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="de6c9-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="de6c9-108">取得到目前為止已載入的模組清單。</span><span class="sxs-lookup"><span data-stu-id="de6c9-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de6c9-109">備註</span><span class="sxs-lookup"><span data-stu-id="de6c9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de6c9-110">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="de6c9-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="de6c9-111">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="de6c9-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6c9-112">需求</span><span class="sxs-lookup"><span data-stu-id="de6c9-112">Requirements</span></span>  
 <span data-ttu-id="de6c9-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de6c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de6c9-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de6c9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de6c9-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de6c9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de6c9-116">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6c9-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6c9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="de6c9-117">See Also</span></span>  
 [<span data-ttu-id="de6c9-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="de6c9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="de6c9-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="de6c9-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
