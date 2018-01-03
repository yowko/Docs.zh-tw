---
title: "ICorDebugDataTarget2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aefdb34277d2cb7ebc29ef817745b85064475d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="291f6-102">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="291f6-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="291f6-103">以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="291f6-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="291f6-104">方法</span><span class="sxs-lookup"><span data-stu-id="291f6-104">Methods</span></span>  
  
|<span data-ttu-id="291f6-105">方法</span><span class="sxs-lookup"><span data-stu-id="291f6-105">Method</span></span>|<span data-ttu-id="291f6-106">描述</span><span class="sxs-lookup"><span data-stu-id="291f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="291f6-107">CreateVirtualUnwinder 方法</span><span class="sxs-lookup"><span data-stu-id="291f6-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="291f6-108">建立新的堆疊 unwinder，以從初始內容 (不一定是執行緒的分葉) 開始回溯。</span><span class="sxs-lookup"><span data-stu-id="291f6-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="291f6-109">EnumerateThreadIDs 方法</span><span class="sxs-lookup"><span data-stu-id="291f6-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="291f6-110">傳回使用中執行緒 ID 的清單。</span><span class="sxs-lookup"><span data-stu-id="291f6-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="291f6-111">GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="291f6-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="291f6-112">從模組中的位址傳回模組基底位址和大小。</span><span class="sxs-lookup"><span data-stu-id="291f6-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="291f6-113">GetImageLocation 方法</span><span class="sxs-lookup"><span data-stu-id="291f6-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="291f6-114">從模組的基底位址傳回模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="291f6-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="291f6-115">GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="291f6-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="291f6-116">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="291f6-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="291f6-117">備註</span><span class="sxs-lookup"><span data-stu-id="291f6-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="291f6-118">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="291f6-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="291f6-119">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="291f6-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="291f6-120">需求</span><span class="sxs-lookup"><span data-stu-id="291f6-120">Requirements</span></span>  
 <span data-ttu-id="291f6-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="291f6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="291f6-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="291f6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="291f6-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="291f6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="291f6-124">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="291f6-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291f6-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="291f6-125">See Also</span></span>  
 [<span data-ttu-id="291f6-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="291f6-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="291f6-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="291f6-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
