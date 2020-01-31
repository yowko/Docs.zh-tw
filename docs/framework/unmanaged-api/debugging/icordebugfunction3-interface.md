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
ms.openlocfilehash: 7ef983c2f0785cb97baf8ba1ad3483b46c08af9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788663"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="3dcd8-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="3dcd8-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="3dcd8-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="3dcd8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3dcd8-104">以邏輯方式延伸 ICorDebugFunction 介面，以提供對 ReJIT 要求之程式碼的存取。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3dcd8-105">方法</span><span class="sxs-lookup"><span data-stu-id="3dcd8-105">Methods</span></span>  
  
|<span data-ttu-id="3dcd8-106">方法</span><span class="sxs-lookup"><span data-stu-id="3dcd8-106">Method</span></span>|<span data-ttu-id="3dcd8-107">描述</span><span class="sxs-lookup"><span data-stu-id="3dcd8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3dcd8-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="3dcd8-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="3dcd8-109">取得[ICorDebugILCode](icordebugilcode-interface.md)的介面指標，其中包含來自作用中 ReJIT 要求的 IL。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dcd8-110">備註</span><span class="sxs-lookup"><span data-stu-id="3dcd8-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dcd8-111">需求</span><span class="sxs-lookup"><span data-stu-id="3dcd8-111">Requirements</span></span>  
 <span data-ttu-id="3dcd8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dcd8-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dcd8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dcd8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dcd8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dcd8-115">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dcd8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcd8-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="3dcd8-116">See also</span></span>

- [<span data-ttu-id="3dcd8-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3dcd8-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3dcd8-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="3dcd8-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="3dcd8-119">ReJIT：使用說明指南</span><span class="sxs-lookup"><span data-stu-id="3dcd8-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
