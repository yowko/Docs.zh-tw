---
title: "ICorDebugAssembly3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e581b4256da2ecc19a8b97520e0e70fef972b549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="6691c-102">ICorDebugAssembly3 介面</span><span class="sxs-lookup"><span data-stu-id="6691c-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="6691c-103">以邏輯方式擴充 ICorDebugAssembly 介面，以提供支援給容器組件及其所包含的組件。</span><span class="sxs-lookup"><span data-stu-id="6691c-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6691c-104">方法</span><span class="sxs-lookup"><span data-stu-id="6691c-104">Methods</span></span>  
  
|<span data-ttu-id="6691c-105">方法</span><span class="sxs-lookup"><span data-stu-id="6691c-105">Method</span></span>|<span data-ttu-id="6691c-106">描述</span><span class="sxs-lookup"><span data-stu-id="6691c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6691c-107">EnumerateContainedAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="6691c-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="6691c-108">取得這個組件所包含之組件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="6691c-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="6691c-109">GetContainerAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="6691c-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="6691c-110">傳回這個 `ICorDebugAssembly3` 物件的容器組件。</span><span class="sxs-lookup"><span data-stu-id="6691c-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6691c-111">備註</span><span class="sxs-lookup"><span data-stu-id="6691c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6691c-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="6691c-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="6691c-113">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="6691c-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6691c-114">需求</span><span class="sxs-lookup"><span data-stu-id="6691c-114">Requirements</span></span>  
 <span data-ttu-id="6691c-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6691c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6691c-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6691c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6691c-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6691c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6691c-118">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6691c-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6691c-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="6691c-119">See Also</span></span>  
 [<span data-ttu-id="6691c-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6691c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6691c-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="6691c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
