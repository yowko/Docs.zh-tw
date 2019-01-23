---
title: ICorDebugInstanceFieldSymbol 介面
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082d8e8c8b57b7d0938f59aebbe08e35a7e3f7df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560727"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="0df07-102">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="0df07-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="0df07-103">代表執行個體欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="0df07-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0df07-104">方法</span><span class="sxs-lookup"><span data-stu-id="0df07-104">Methods</span></span>  
  
|<span data-ttu-id="0df07-105">方法</span><span class="sxs-lookup"><span data-stu-id="0df07-105">Method</span></span>|<span data-ttu-id="0df07-106">描述</span><span class="sxs-lookup"><span data-stu-id="0df07-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0df07-107">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="0df07-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="0df07-108">取得執行個體欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="0df07-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="0df07-109">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="0df07-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="0df07-110">取得此執行個體欄位在其父類別中的位移 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="0df07-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="0df07-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="0df07-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="0df07-112">取得執行個體欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="0df07-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0df07-113">備註</span><span class="sxs-lookup"><span data-stu-id="0df07-113">Remarks</span></span>  
 <span data-ttu-id="0df07-114">`ICorDebugInstanceFieldSymbol` 介面用來擷取執行個體欄位的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="0df07-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0df07-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="0df07-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0df07-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="0df07-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0df07-117">需求</span><span class="sxs-lookup"><span data-stu-id="0df07-117">Requirements</span></span>  
 <span data-ttu-id="0df07-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0df07-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df07-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0df07-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0df07-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0df07-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0df07-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df07-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df07-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0df07-122">See also</span></span>
- [<span data-ttu-id="0df07-123">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="0df07-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="0df07-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0df07-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0df07-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="0df07-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
