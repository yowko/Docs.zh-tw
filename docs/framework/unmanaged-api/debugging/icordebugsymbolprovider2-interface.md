---
title: ICorDebugSymbolProvider2 介面
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b787302902779695c48df6e02e2ee00b28f44cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142463"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="abe4e-102">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="abe4e-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="abe4e-103">以邏輯方式擴充[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)來擷取其他偵錯符號資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="abe4e-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="abe4e-104">方法</span><span class="sxs-lookup"><span data-stu-id="abe4e-104">Methods</span></span>  
  
|<span data-ttu-id="abe4e-105">方法</span><span class="sxs-lookup"><span data-stu-id="abe4e-105">Method</span></span>|<span data-ttu-id="abe4e-106">描述</span><span class="sxs-lookup"><span data-stu-id="abe4e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="abe4e-107">GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="abe4e-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="abe4e-108">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="abe4e-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="abe4e-109">GetGenericDictionaryInfo 方法</span><span class="sxs-lookup"><span data-stu-id="abe4e-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="abe4e-110">擷取泛型字典對應。</span><span class="sxs-lookup"><span data-stu-id="abe4e-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abe4e-111">備註</span><span class="sxs-lookup"><span data-stu-id="abe4e-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abe4e-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="abe4e-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="abe4e-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="abe4e-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe4e-114">需求</span><span class="sxs-lookup"><span data-stu-id="abe4e-114">Requirements</span></span>  
 <span data-ttu-id="abe4e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abe4e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe4e-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abe4e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abe4e-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe4e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe4e-118">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe4e-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe4e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abe4e-119">See also</span></span>

- [<span data-ttu-id="abe4e-120">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="abe4e-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="abe4e-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="abe4e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="abe4e-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="abe4e-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
