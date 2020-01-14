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
ms.openlocfilehash: b74008e0a183d46d82c5262209d582537fd155c7
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938078"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="02444-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="02444-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="02444-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="02444-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="02444-104">以邏輯方式延伸 ICorDebugFunction 介面，以提供對 ReJIT 要求之程式碼的存取。</span><span class="sxs-lookup"><span data-stu-id="02444-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02444-105">方法</span><span class="sxs-lookup"><span data-stu-id="02444-105">Methods</span></span>  
  
|<span data-ttu-id="02444-106">方法</span><span class="sxs-lookup"><span data-stu-id="02444-106">Method</span></span>|<span data-ttu-id="02444-107">描述</span><span class="sxs-lookup"><span data-stu-id="02444-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02444-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="02444-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="02444-109">取得[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)的介面指標，其中包含來自作用中 ReJIT 要求的 IL。</span><span class="sxs-lookup"><span data-stu-id="02444-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02444-110">備註</span><span class="sxs-lookup"><span data-stu-id="02444-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02444-111">需求</span><span class="sxs-lookup"><span data-stu-id="02444-111">Requirements</span></span>  
 <span data-ttu-id="02444-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02444-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02444-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02444-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02444-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02444-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02444-115">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02444-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02444-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="02444-116">See also</span></span>

- [<span data-ttu-id="02444-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="02444-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="02444-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="02444-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="02444-119">ReJIT：使用說明指南</span><span class="sxs-lookup"><span data-stu-id="02444-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
