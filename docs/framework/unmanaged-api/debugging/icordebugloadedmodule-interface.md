---
title: ICorDebugLoadedModule 介面
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946280"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="77fd4-102">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="77fd4-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="77fd4-103">提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="77fd4-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77fd4-104">方法</span><span class="sxs-lookup"><span data-stu-id="77fd4-104">Methods</span></span>  
  
|<span data-ttu-id="77fd4-105">方法</span><span class="sxs-lookup"><span data-stu-id="77fd4-105">Method</span></span>|<span data-ttu-id="77fd4-106">描述</span><span class="sxs-lookup"><span data-stu-id="77fd4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77fd4-107">GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="77fd4-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="77fd4-108">取得載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="77fd4-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="77fd4-109">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="77fd4-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="77fd4-110">取得載入模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="77fd4-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="77fd4-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="77fd4-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="77fd4-112">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="77fd4-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77fd4-113">備註</span><span class="sxs-lookup"><span data-stu-id="77fd4-113">Remarks</span></span>  
 <span data-ttu-id="77fd4-114">`ICorDebugLoadedModule` 介面是由偵錯工具實作，並由 CLR 偵錯介面用以從偵錯工具取得載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="77fd4-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77fd4-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="77fd4-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="77fd4-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="77fd4-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77fd4-117">需求</span><span class="sxs-lookup"><span data-stu-id="77fd4-117">Requirements</span></span>  
 <span data-ttu-id="77fd4-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77fd4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77fd4-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77fd4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77fd4-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77fd4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77fd4-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77fd4-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fd4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77fd4-122">See also</span></span>

- [<span data-ttu-id="77fd4-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="77fd4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="77fd4-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="77fd4-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
