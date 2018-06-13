---
title: ICorDebugSymbolProvider2 介面
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db1bba48f4685338f4531e2c11506de338e5c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423217"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="9110c-102">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="9110c-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="9110c-103">以邏輯方式擴充[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)介面，以擷取其他偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="9110c-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9110c-104">方法</span><span class="sxs-lookup"><span data-stu-id="9110c-104">Methods</span></span>  
  
|<span data-ttu-id="9110c-105">方法</span><span class="sxs-lookup"><span data-stu-id="9110c-105">Method</span></span>|<span data-ttu-id="9110c-106">描述</span><span class="sxs-lookup"><span data-stu-id="9110c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9110c-107">GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="9110c-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="9110c-108">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="9110c-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="9110c-109">GetGenericDictionaryInfo 方法</span><span class="sxs-lookup"><span data-stu-id="9110c-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="9110c-110">擷取泛型字典對應。</span><span class="sxs-lookup"><span data-stu-id="9110c-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9110c-111">備註</span><span class="sxs-lookup"><span data-stu-id="9110c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9110c-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="9110c-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9110c-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="9110c-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9110c-114">需求</span><span class="sxs-lookup"><span data-stu-id="9110c-114">Requirements</span></span>  
 <span data-ttu-id="9110c-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9110c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9110c-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9110c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9110c-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9110c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9110c-118">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9110c-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9110c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9110c-119">See Also</span></span>  
 [<span data-ttu-id="9110c-120">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="9110c-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="9110c-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9110c-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9110c-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="9110c-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
