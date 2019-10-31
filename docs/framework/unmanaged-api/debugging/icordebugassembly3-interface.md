---
title: ICorDebugAssembly3 介面
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 930101f6cd4ebb9215d6420f774b8e066c54a4f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095371"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="e8534-102">ICorDebugAssembly3 介面</span><span class="sxs-lookup"><span data-stu-id="e8534-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="e8534-103">以邏輯方式擴充 ICorDebugAssembly 介面，以提供容器元件和其包含元件的支援。</span><span class="sxs-lookup"><span data-stu-id="e8534-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8534-104">方法</span><span class="sxs-lookup"><span data-stu-id="e8534-104">Methods</span></span>  
  
|<span data-ttu-id="e8534-105">方法</span><span class="sxs-lookup"><span data-stu-id="e8534-105">Method</span></span>|<span data-ttu-id="e8534-106">描述</span><span class="sxs-lookup"><span data-stu-id="e8534-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8534-107">EnumerateContainedAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="e8534-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="e8534-108">取得這個組件所包含之組件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e8534-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="e8534-109">GetContainerAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="e8534-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="e8534-110">傳回這個 `ICorDebugAssembly3` 物件的容器組件。</span><span class="sxs-lookup"><span data-stu-id="e8534-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8534-111">備註</span><span class="sxs-lookup"><span data-stu-id="e8534-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8534-112">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e8534-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="e8534-113">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="e8534-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8534-114">需求</span><span class="sxs-lookup"><span data-stu-id="e8534-114">Requirements</span></span>  
 <span data-ttu-id="e8534-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8534-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8534-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8534-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8534-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8534-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8534-118">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8534-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8534-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8534-119">See also</span></span>

- [<span data-ttu-id="e8534-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e8534-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e8534-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="e8534-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
