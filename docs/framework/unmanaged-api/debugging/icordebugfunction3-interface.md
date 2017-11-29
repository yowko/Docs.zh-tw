---
title: "ICorDebugFunction3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction3
api_location: mscordbi.dll
api_type: COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfe0c420c1c9b8074b7cb769e592f8cb2f5916e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="55cc7-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="55cc7-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="55cc7-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="55cc7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="55cc7-104">以邏輯方式擴充 ICorDebugFunction 介面，以提供對 ReJIT 要求從程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="55cc7-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55cc7-105">方法</span><span class="sxs-lookup"><span data-stu-id="55cc7-105">Methods</span></span>  
  
|<span data-ttu-id="55cc7-106">方法</span><span class="sxs-lookup"><span data-stu-id="55cc7-106">Method</span></span>|<span data-ttu-id="55cc7-107">說明</span><span class="sxs-lookup"><span data-stu-id="55cc7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55cc7-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="55cc7-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="55cc7-109">取得的介面指標[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) ，其中包含從作用中 ReJIT 要求之 IL。</span><span class="sxs-lookup"><span data-stu-id="55cc7-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55cc7-110">備註</span><span class="sxs-lookup"><span data-stu-id="55cc7-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55cc7-111">需求</span><span class="sxs-lookup"><span data-stu-id="55cc7-111">Requirements</span></span>  
 <span data-ttu-id="55cc7-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55cc7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55cc7-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55cc7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55cc7-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55cc7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55cc7-115">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55cc7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cc7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55cc7-116">See Also</span></span>  
 [<span data-ttu-id="55cc7-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="55cc7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="55cc7-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="55cc7-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="55cc7-119">ReJIT： 使用說明指南</span><span class="sxs-lookup"><span data-stu-id="55cc7-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
