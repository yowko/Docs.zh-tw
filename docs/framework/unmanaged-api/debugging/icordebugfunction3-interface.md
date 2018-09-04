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
ms.openlocfilehash: ff49d64b0b58d301d24e39bc626abf6520c031b9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514216"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="6d571-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="6d571-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="6d571-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="6d571-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6d571-104">以邏輯方式擴充 ICorDebugFunction 介面，以提供存取 ReJIT 要求從程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d571-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d571-105">方法</span><span class="sxs-lookup"><span data-stu-id="6d571-105">Methods</span></span>  
  
|<span data-ttu-id="6d571-106">方法</span><span class="sxs-lookup"><span data-stu-id="6d571-106">Method</span></span>|<span data-ttu-id="6d571-107">描述</span><span class="sxs-lookup"><span data-stu-id="6d571-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d571-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="6d571-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="6d571-109">取得的介面指標[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) ，其中包含作用中 ReJIT 要求之 IL。</span><span class="sxs-lookup"><span data-stu-id="6d571-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d571-110">備註</span><span class="sxs-lookup"><span data-stu-id="6d571-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d571-111">需求</span><span class="sxs-lookup"><span data-stu-id="6d571-111">Requirements</span></span>  
 <span data-ttu-id="6d571-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d571-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d571-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d571-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d571-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d571-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d571-115">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d571-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d571-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d571-116">See Also</span></span>  
 [<span data-ttu-id="6d571-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6d571-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6d571-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="6d571-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="6d571-119">ReJIT： 使用說明指南</span><span class="sxs-lookup"><span data-stu-id="6d571-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
