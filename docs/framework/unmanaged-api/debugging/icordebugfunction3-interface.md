---
title: "ICorDebugFunction3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28d2d0d1058dae69bc17e370cc42ed56dc35b0e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="b7031-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="b7031-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="b7031-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="b7031-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b7031-104">以邏輯方式擴充 ICorDebugFunction 介面，以提供對 ReJIT 要求從程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="b7031-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7031-105">方法</span><span class="sxs-lookup"><span data-stu-id="b7031-105">Methods</span></span>  
  
|<span data-ttu-id="b7031-106">方法</span><span class="sxs-lookup"><span data-stu-id="b7031-106">Method</span></span>|<span data-ttu-id="b7031-107">描述</span><span class="sxs-lookup"><span data-stu-id="b7031-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7031-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="b7031-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="b7031-109">取得的介面指標[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) ，其中包含從作用中 ReJIT 要求之 IL。</span><span class="sxs-lookup"><span data-stu-id="b7031-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7031-110">備註</span><span class="sxs-lookup"><span data-stu-id="b7031-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7031-111">需求</span><span class="sxs-lookup"><span data-stu-id="b7031-111">Requirements</span></span>  
 <span data-ttu-id="b7031-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7031-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7031-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7031-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7031-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7031-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7031-115">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7031-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7031-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7031-116">See Also</span></span>  
 [<span data-ttu-id="b7031-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b7031-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b7031-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="b7031-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="b7031-119">ReJIT： 使用說明指南</span><span class="sxs-lookup"><span data-stu-id="b7031-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
