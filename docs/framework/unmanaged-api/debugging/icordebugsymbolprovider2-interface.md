---
title: "ICorDebugSymbolProvider2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7666b8d64b689d3640594f07614be97b72e85a8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="8633d-102">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="8633d-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="8633d-103">以邏輯方式擴充[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)介面，以擷取其他偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="8633d-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8633d-104">方法</span><span class="sxs-lookup"><span data-stu-id="8633d-104">Methods</span></span>  
  
|<span data-ttu-id="8633d-105">方法</span><span class="sxs-lookup"><span data-stu-id="8633d-105">Method</span></span>|<span data-ttu-id="8633d-106">描述</span><span class="sxs-lookup"><span data-stu-id="8633d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8633d-107">GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="8633d-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="8633d-108">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="8633d-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="8633d-109">GetGenericDictionaryInfo 方法</span><span class="sxs-lookup"><span data-stu-id="8633d-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="8633d-110">擷取泛型字典對應。</span><span class="sxs-lookup"><span data-stu-id="8633d-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8633d-111">備註</span><span class="sxs-lookup"><span data-stu-id="8633d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8633d-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="8633d-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8633d-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="8633d-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8633d-114">需求</span><span class="sxs-lookup"><span data-stu-id="8633d-114">Requirements</span></span>  
 <span data-ttu-id="8633d-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8633d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8633d-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8633d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8633d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8633d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8633d-118">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8633d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8633d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="8633d-119">See Also</span></span>  
 [<span data-ttu-id="8633d-120">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="8633d-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="8633d-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8633d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8633d-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="8633d-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
