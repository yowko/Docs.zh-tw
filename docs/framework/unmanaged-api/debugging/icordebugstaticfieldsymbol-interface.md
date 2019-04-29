---
title: ICorDebugStaticFieldSymbol 介面
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 382f3fc9377c25379809badac0bc580c3593cbde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782586"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="cddbe-102">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="cddbe-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="cddbe-103">代表靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="cddbe-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cddbe-104">方法</span><span class="sxs-lookup"><span data-stu-id="cddbe-104">Methods</span></span>  
  
|<span data-ttu-id="cddbe-105">方法</span><span class="sxs-lookup"><span data-stu-id="cddbe-105">Method</span></span>|<span data-ttu-id="cddbe-106">描述</span><span class="sxs-lookup"><span data-stu-id="cddbe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cddbe-107">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="cddbe-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="cddbe-108">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="cddbe-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="cddbe-109">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="cddbe-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="cddbe-110">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="cddbe-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="cddbe-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="cddbe-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="cddbe-112">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="cddbe-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cddbe-113">備註</span><span class="sxs-lookup"><span data-stu-id="cddbe-113">Remarks</span></span>  
 <span data-ttu-id="cddbe-114">`ICorDebugStaticFieldSymbol` 介面可用來擷取靜態欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="cddbe-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cddbe-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="cddbe-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="cddbe-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="cddbe-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cddbe-117">需求</span><span class="sxs-lookup"><span data-stu-id="cddbe-117">Requirements</span></span>  
 <span data-ttu-id="cddbe-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cddbe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cddbe-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cddbe-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cddbe-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cddbe-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cddbe-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cddbe-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddbe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cddbe-122">See also</span></span>

- [<span data-ttu-id="cddbe-123">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="cddbe-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="cddbe-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cddbe-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cddbe-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="cddbe-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
