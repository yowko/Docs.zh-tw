---
title: ICorDebugLoadedModule 介面
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200749"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="9cdb3-102">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="9cdb3-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="9cdb3-103">提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9cdb3-104">方法</span><span class="sxs-lookup"><span data-stu-id="9cdb3-104">Methods</span></span>  
  
|<span data-ttu-id="9cdb3-105">方法</span><span class="sxs-lookup"><span data-stu-id="9cdb3-105">Method</span></span>|<span data-ttu-id="9cdb3-106">描述</span><span class="sxs-lookup"><span data-stu-id="9cdb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9cdb3-107">GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="9cdb3-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="9cdb3-108">取得載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="9cdb3-109">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="9cdb3-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="9cdb3-110">取得載入模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="9cdb3-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="9cdb3-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="9cdb3-112">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cdb3-113">備註</span><span class="sxs-lookup"><span data-stu-id="9cdb3-113">Remarks</span></span>  
 <span data-ttu-id="9cdb3-114">`ICorDebugLoadedModule` 介面是由偵錯工具實作，並由 CLR 偵錯介面用以從偵錯工具取得載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cdb3-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9cdb3-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cdb3-117">需求</span><span class="sxs-lookup"><span data-stu-id="9cdb3-117">Requirements</span></span>  
 <span data-ttu-id="9cdb3-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cdb3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cdb3-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cdb3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cdb3-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cdb3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cdb3-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cdb3-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdb3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cdb3-122">See also</span></span>

- [<span data-ttu-id="9cdb3-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9cdb3-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9cdb3-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="9cdb3-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
