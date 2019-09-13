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
ms.openlocfilehash: a3eebdf56796fe599ec6ff62d7008d1af3be796e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926841"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="051a6-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="051a6-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="051a6-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="051a6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="051a6-104">以邏輯方式擴充 ICorDebugFunction 介面，以提供對 ReJIT 要求之程式碼的存取權。</span><span class="sxs-lookup"><span data-stu-id="051a6-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="051a6-105">方法</span><span class="sxs-lookup"><span data-stu-id="051a6-105">Methods</span></span>  
  
|<span data-ttu-id="051a6-106">方法</span><span class="sxs-lookup"><span data-stu-id="051a6-106">Method</span></span>|<span data-ttu-id="051a6-107">描述</span><span class="sxs-lookup"><span data-stu-id="051a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="051a6-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="051a6-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="051a6-109">取得[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)的介面指標，其中包含來自作用中 ReJIT 要求的 IL。</span><span class="sxs-lookup"><span data-stu-id="051a6-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="051a6-110">備註</span><span class="sxs-lookup"><span data-stu-id="051a6-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="051a6-111">需求</span><span class="sxs-lookup"><span data-stu-id="051a6-111">Requirements</span></span>  
 <span data-ttu-id="051a6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="051a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="051a6-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="051a6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="051a6-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="051a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="051a6-115">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="051a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051a6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="051a6-116">See also</span></span>

- [<span data-ttu-id="051a6-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="051a6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="051a6-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="051a6-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="051a6-119">ReJIT使用說明指南</span><span class="sxs-lookup"><span data-stu-id="051a6-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
