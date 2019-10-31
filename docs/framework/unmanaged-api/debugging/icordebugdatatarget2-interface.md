---
title: ICorDebugDataTarget2 介面
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 3c59752949ca29cbd0ed5a34ec7aeb3d98b6f9b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136488"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="877d7-102">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="877d7-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="877d7-103">以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="877d7-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="877d7-104">方法</span><span class="sxs-lookup"><span data-stu-id="877d7-104">Methods</span></span>  
  
|<span data-ttu-id="877d7-105">方法</span><span class="sxs-lookup"><span data-stu-id="877d7-105">Method</span></span>|<span data-ttu-id="877d7-106">描述</span><span class="sxs-lookup"><span data-stu-id="877d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="877d7-107">CreateVirtualUnwinder 方法</span><span class="sxs-lookup"><span data-stu-id="877d7-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="877d7-108">建立新的堆疊 unwinder，以從初始內容 (不一定是執行緒的分葉) 開始回溯。</span><span class="sxs-lookup"><span data-stu-id="877d7-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="877d7-109">EnumerateThreadIDs 方法</span><span class="sxs-lookup"><span data-stu-id="877d7-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="877d7-110">傳回使用中執行緒 ID 的清單。</span><span class="sxs-lookup"><span data-stu-id="877d7-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="877d7-111">GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="877d7-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="877d7-112">從模組中的位址傳回模組基底位址和大小。</span><span class="sxs-lookup"><span data-stu-id="877d7-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="877d7-113">GetImageLocation 方法</span><span class="sxs-lookup"><span data-stu-id="877d7-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="877d7-114">從模組的基底位址傳回模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="877d7-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="877d7-115">GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="877d7-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="877d7-116">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="877d7-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="877d7-117">備註</span><span class="sxs-lookup"><span data-stu-id="877d7-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="877d7-118">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="877d7-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="877d7-119">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="877d7-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="877d7-120">需求</span><span class="sxs-lookup"><span data-stu-id="877d7-120">Requirements</span></span>  
 <span data-ttu-id="877d7-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="877d7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="877d7-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="877d7-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="877d7-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="877d7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="877d7-124">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="877d7-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877d7-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="877d7-125">See also</span></span>

- [<span data-ttu-id="877d7-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="877d7-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="877d7-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="877d7-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
