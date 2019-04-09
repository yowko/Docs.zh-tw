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
ms.openlocfilehash: 4c29d631f84ce2dd7532e32951e71d6597218ebb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088856"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="da4c3-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="da4c3-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="da4c3-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="da4c3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="da4c3-104">以邏輯方式擴充 ICorDebugFunction 介面，以提供存取 ReJIT 要求從程式碼。</span><span class="sxs-lookup"><span data-stu-id="da4c3-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da4c3-105">方法</span><span class="sxs-lookup"><span data-stu-id="da4c3-105">Methods</span></span>  
  
|<span data-ttu-id="da4c3-106">方法</span><span class="sxs-lookup"><span data-stu-id="da4c3-106">Method</span></span>|<span data-ttu-id="da4c3-107">描述</span><span class="sxs-lookup"><span data-stu-id="da4c3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da4c3-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="da4c3-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="da4c3-109">取得的介面指標[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) ，其中包含作用中 ReJIT 要求之 IL。</span><span class="sxs-lookup"><span data-stu-id="da4c3-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da4c3-110">備註</span><span class="sxs-lookup"><span data-stu-id="da4c3-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4c3-111">需求</span><span class="sxs-lookup"><span data-stu-id="da4c3-111">Requirements</span></span>  
 <span data-ttu-id="da4c3-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da4c3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da4c3-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da4c3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da4c3-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da4c3-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="da4c3-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="da4c3-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="da4c3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da4c3-116">See also</span></span>

- [<span data-ttu-id="da4c3-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="da4c3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="da4c3-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="da4c3-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="da4c3-119">ReJIT:操作說明指南</span><span class="sxs-lookup"><span data-stu-id="da4c3-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
