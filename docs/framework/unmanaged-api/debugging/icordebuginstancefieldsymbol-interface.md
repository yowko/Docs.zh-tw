---
title: ICorDebugInstanceFieldSymbol 介面
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e5f63df9354df6a4d142c2f6ae12f9a0d5600fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910145"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="548ea-102">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="548ea-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="548ea-103">代表執行個體欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="548ea-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="548ea-104">方法</span><span class="sxs-lookup"><span data-stu-id="548ea-104">Methods</span></span>  
  
|<span data-ttu-id="548ea-105">方法</span><span class="sxs-lookup"><span data-stu-id="548ea-105">Method</span></span>|<span data-ttu-id="548ea-106">描述</span><span class="sxs-lookup"><span data-stu-id="548ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="548ea-107">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="548ea-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="548ea-108">取得執行個體欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="548ea-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="548ea-109">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="548ea-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="548ea-110">取得在父類別中此執行個體欄位之位元組的位移。</span><span class="sxs-lookup"><span data-stu-id="548ea-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="548ea-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="548ea-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="548ea-112">取得執行個體欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="548ea-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="548ea-113">備註</span><span class="sxs-lookup"><span data-stu-id="548ea-113">Remarks</span></span>  
 <span data-ttu-id="548ea-114">`ICorDebugInstanceFieldSymbol` 介面用來擷取執行個體欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="548ea-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="548ea-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="548ea-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="548ea-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="548ea-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="548ea-117">需求</span><span class="sxs-lookup"><span data-stu-id="548ea-117">Requirements</span></span>  
 <span data-ttu-id="548ea-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="548ea-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="548ea-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="548ea-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="548ea-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="548ea-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="548ea-121">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="548ea-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548ea-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="548ea-122">See also</span></span>

- [<span data-ttu-id="548ea-123">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="548ea-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="548ea-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="548ea-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="548ea-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="548ea-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
