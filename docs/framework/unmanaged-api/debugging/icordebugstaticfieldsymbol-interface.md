---
title: ICorDebugStaticFieldSymbol 介面
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: 0891df1fc0528ff485605b2c4168fcff0adff990
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131711"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="18d89-102">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="18d89-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="18d89-103">代表靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="18d89-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18d89-104">方法</span><span class="sxs-lookup"><span data-stu-id="18d89-104">Methods</span></span>  
  
|<span data-ttu-id="18d89-105">方法</span><span class="sxs-lookup"><span data-stu-id="18d89-105">Method</span></span>|<span data-ttu-id="18d89-106">描述</span><span class="sxs-lookup"><span data-stu-id="18d89-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18d89-107">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="18d89-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="18d89-108">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="18d89-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="18d89-109">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="18d89-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="18d89-110">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="18d89-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="18d89-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="18d89-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="18d89-112">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="18d89-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18d89-113">備註</span><span class="sxs-lookup"><span data-stu-id="18d89-113">Remarks</span></span>  
 <span data-ttu-id="18d89-114">`ICorDebugStaticFieldSymbol` 介面可用來擷取靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="18d89-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18d89-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="18d89-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="18d89-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="18d89-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18d89-117">需求</span><span class="sxs-lookup"><span data-stu-id="18d89-117">Requirements</span></span>  
 <span data-ttu-id="18d89-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18d89-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18d89-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18d89-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18d89-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18d89-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18d89-121">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18d89-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d89-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="18d89-122">See also</span></span>

- [<span data-ttu-id="18d89-123">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="18d89-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="18d89-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="18d89-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="18d89-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="18d89-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
