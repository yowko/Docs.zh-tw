---
title: ICorDebugDataTarget3 介面
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965200"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="9d229-102">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="9d229-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="9d229-103">以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以提供已載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9d229-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="9d229-104">方法</span><span class="sxs-lookup"><span data-stu-id="9d229-104">Method</span></span>  
  
|<span data-ttu-id="9d229-105">方法</span><span class="sxs-lookup"><span data-stu-id="9d229-105">Method</span></span>|<span data-ttu-id="9d229-106">描述</span><span class="sxs-lookup"><span data-stu-id="9d229-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d229-107">GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="9d229-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="9d229-108">取得到目前為止已載入的模組清單。</span><span class="sxs-lookup"><span data-stu-id="9d229-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d229-109">備註</span><span class="sxs-lookup"><span data-stu-id="9d229-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d229-110">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="9d229-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9d229-111">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="9d229-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d229-112">需求</span><span class="sxs-lookup"><span data-stu-id="9d229-112">Requirements</span></span>  
 <span data-ttu-id="9d229-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d229-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d229-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d229-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d229-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d229-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d229-116">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d229-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d229-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d229-117">See also</span></span>

- [<span data-ttu-id="9d229-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9d229-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9d229-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="9d229-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
