---
title: ICorDebugFunction3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e564ce63f7bf9e04ebf9a0bdcfc819ea23b3b2ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515556"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="133f8-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="133f8-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="133f8-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="133f8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="133f8-104">以邏輯方式擴充 ICorDebugFunction 介面，以提供存取 ReJIT 要求從程式碼。</span><span class="sxs-lookup"><span data-stu-id="133f8-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="133f8-105">方法</span><span class="sxs-lookup"><span data-stu-id="133f8-105">Methods</span></span>  
  
|<span data-ttu-id="133f8-106">方法</span><span class="sxs-lookup"><span data-stu-id="133f8-106">Method</span></span>|<span data-ttu-id="133f8-107">描述</span><span class="sxs-lookup"><span data-stu-id="133f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="133f8-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="133f8-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="133f8-109">取得的介面指標[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) ，其中包含作用中 ReJIT 要求之 IL。</span><span class="sxs-lookup"><span data-stu-id="133f8-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="133f8-110">備註</span><span class="sxs-lookup"><span data-stu-id="133f8-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="133f8-111">需求</span><span class="sxs-lookup"><span data-stu-id="133f8-111">Requirements</span></span>  
 <span data-ttu-id="133f8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="133f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="133f8-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="133f8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="133f8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="133f8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="133f8-115">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="133f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133f8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="133f8-116">See also</span></span>
- [<span data-ttu-id="133f8-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="133f8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="133f8-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="133f8-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="133f8-119">ReJIT:操作說明指南</span><span class="sxs-lookup"><span data-stu-id="133f8-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
